<template>
  <div class="detail">
    <div class="header">
      {{JdDataDetail.title}}
    </div>
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span><a :href="JdDataDetail.sell_url" target="_blank">{{JdDataDetail.title}}</a></span>
      </div>
      <div class="text item">
        <span class="price">
          京东价：
          <span>{{JdDataDetail.price}}</span>
        </span>
        <span>作者：{{JdDataDetail.author}}</span>
        &nbsp;
        <br>
        <span>出版社：{{JdDataDetail.pub}}</span>
        &nbsp;
        <br>
        <div class="book-info">
          <span class="tmp">书籍简介：</span>
          <div class="content">{{JdDataDetail.book_info}}</div>
        </div>
      </div>
    </el-card>
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span><a :href="DangDataDetail.sell_url" target="_blank">{{DangDataDetail.title}}</a></span>
      </div>
      <div class="text item">
        <span class="price">
          当当价：
          <span>{{JdDataDetail.price}}</span>
        </span>
        <span>作者：{{DangDataDetail.author}}</span>
        &nbsp;
        <br>
        <span>出版社：{{DangDataDetail.pub}}</span>
        &nbsp;
        <br>
        <div class="book-info">
          <span class="tmp">书籍简介：</span>
          <div class="content">{{DangDataDetail.content}}</div>
        </div>
      </div>
    </el-card>
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span><a :href="BooksChinaDetail.sell_url" target="_blank">{{BooksChinaDetail.title}}</a></span>
      </div>
      <div class="text item">
        <span class="price">
          中国图书网价：
          <span>{{JdDataDetail.price}}</span>
        </span>
        <span>作者：{{BooksChinaDetail.author}}</span>
        &nbsp;
        <br>
        <span>出版社：{{BooksChinaDetail.pub}}</span>
        &nbsp;
        <br>
        <div class="book-info">
          <span class="tmp">书籍简介：</span>
          <div class="content">{{BooksChinaDetail.brief}}</div>
        </div>
      </div>
    </el-card>
  </div>
</template>

<script>
export default {
  name: 'Detail',
  data () {
    return {
      JdDataDetail: [],
      DangDataDetail: [],
      BooksChinaDetail: [],
    }
  },
  mounted () {
    var par = this.$route.params.bookname
    this.$axios.get(`/api/detail/jd/${par}`).then(res => {
      this.JdDataDetail = res.data
      var arrLen = Object.keys(res.data)
      this.JdLen = arrLen.length
    }).catch(error => {
      console.log('请求出错' + error)
    })
    this.$axios.get(`/api/detail/dang/${par}`).then(res => {
      this.DangDataDetail = res.data
      var arrLen = Object.keys(res.data)
      this.DangLen = arrLen.length
    }).catch(error => {
      console.log('请求出错' + error)
    })
    this.$axios.get(`/api/detail/chinabook/${par}`).then(res => {
      this.BooksChinaDetail = res.data
      var arrLen = Object.keys(res.data)
      this.BooksChinaLen = arrLen.length
    }).catch(error => {
      console.log('请求出错' + error)
    })
  }
}
</script>

<style scoped>
  .detail {
    display: flex;
    flex-wrap: wrap;
    background: #f1efe9;
  }
  .header {
    width: 100%;
    line-height: 120px;
    font-size: 35px;
    font-weight:bold;
    font-family: 楷体;
  }
  .box-card {
    float: left;
    margin: auto;
    background: #E0DDD4;
    box-shadow: 5px 15px 15px rgba(0,0,0,0.2);
  }
  .content {
    height: 300px;
    overflow: hidden;
    text-align: left;
    text-overflow: ellipsis;
    white-space: normal;
    direction:rtl;
  }
  a {
    color: #2c3e50;
    text-decoration: none;
  }
  a:hover{
    color: darkred;
  }
  .tmp {
    text-align: center;
  }
  .book-info {
    text-align: left;
    line-height: 2;
    font-size: 14px;
  }
  .text {
    position: relative;
    font-size: 14px;
  }
  .text .price{
    position: absolute;
    right: 0px;
    top: -13px;
  }
  .text .price span {
    color:red;
    font-size: 22px;
  }
.text span {
  line-height: 2;
  font-size: 14px;
}
  .item {
    margin-bottom: 18px;
    text-align: left;
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
