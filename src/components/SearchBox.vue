<template>
  <div class="search-box">
    <h2>图书比价搜索系统</h2>
    <el-input placeholder="请输入书名" class="input-with-select" v-model="input"></el-input>
          <el-button  icon="el-icon-search" @click="hrefClick(input)"></el-button>
    <CardBox/>
  </div>
</template>

<script>
import CardBox from '@/components/CardBox'

export default {
  name: 'SearcheBox',
  data () {
    return {
      input: ''
    }
  },
  components: {
    CardBox
  },
  methods: {
    hrefClick (input) {
      this.$router.push({ path: `/detail/${input}` })
    }
  }
}
</script>

<style scoped>
  .search-box {
    margin-top: 15px;
  }
  h2 {
    margin: 40px 0;
  }
  .input-with-select {
    width: 50%;
  }
</style>
