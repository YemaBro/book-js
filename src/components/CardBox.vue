<template>
  <div class="card">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>京东图书</span>
      </div>
      <div v-for="(jd,index) in JdData" :key="index" class="text item">
        <div class="book-title">
          <span class="book-list"><a :href="jd.sell_url" target="_blank">{{jd.rank+'.'}}{{jd.title}}</a></span>
        </div>
        <span class="price-list">{{jd.price}}</span>
      </div>
    </el-card>
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>当当图书</span>
      </div>
      <div v-for="(dang,index) in DangData" :key="index" class="text item">
        <div class="book-title">
          <span class="book-list"><a :href="dang.sell_url" target="_blank">{{dang.rank+'.'}}{{dang.title}}</a></span>
        </div>
        <span class="price-list">{{dang.price}}</span>
      </div>
    </el-card>
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>中国图书网</span>
      </div>
      <div v-for="(china ,index) in BooksChina" :key="index" class="text item">
        <div class="book-title">
          <span class="book-list"><a :href="china.sell_url" target="_blank">{{china.rank+'.'}}{{china.title}}</a></span>
        </div>
        <span class="price-list">{{china.price}}</span>
      </div>
    </el-card>
  </div>
</template>

<script>
export default {
  name: 'CardBox',
  data () {
    return {
      JdData: [],
      DangData: [],
      BooksChina: []
    }
  },
  mounted () {
    this.$axios.get('/api/rank/jd').then(res => {
      this.JdData = res.data
      // console.log(this.JdData)
    }).catch(error => {
      console.log('请求出错' + error)
    })
    this.$axios.get('/api/rank/dang').then(res => {
      this.DangData = res.data
    }).catch(error => {
      console.log('请求出错' + error)
    })
    this.$axios.get('/api/rank/china').then(res => {
      this.BooksChina = res.data
    }).catch(error => {
      console.log('请求出错' + error)
    })
  }
}
</script>

<style scoped>
  .card {
    margin-top: 100px;
    display: flex;
    flex-wrap: wrap;
  }
  .box-card {
    float: left;
    margin: auto;
  }
  .book-title {
    width: 300px;
    overflow: hidden;
    text-align: left;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .book-list {
    width: 5px;
    height: 5px;
  }
  a {
    color: #2c3e50;
    text-decoration: none;
  }
  a:hover{
    color: darkred;
  }
  .price-list {
    /*display: block;*/
    float: right;
  }
  .text {
    font-size: 14px;
  }

  .item {
    margin-bottom: 18px;
  }

  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }
  .clearfix:after {
    clear: both
  }

  .box-card {
    width: 480px;
  }
</style>
