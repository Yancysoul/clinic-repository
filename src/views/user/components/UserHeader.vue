<template>
  <div class="userHeader">
    <el-button type="danger" :size="size">删除</el-button>
    <el-button type="primary" :size="size" @click="addUser">新增</el-button>
    <div class="query">
      <el-input :size="size" placeholder="请输入搜索内容"></el-input>
    </div>
    <el-button type="success" :size="size">查询</el-button>
  </div>
</template>

<script>
export default {
  name: 'UserHeader',
  data () {
    return {
      size: 'mini'
    }
  },
  methods: {
    addUser () {
      this.$store.dispatch('SetUserTitle', '新增人员')
      this.$store.dispatch('SetUserDialog', true)
      this.$store.dispatch('SetUserForm', {})
    }
  }
}
</script>

<style scoped lang="scss">
.userHeader {
  display: flex;
  align-items: center;
  .query {
    width: 250px;
    margin: 0 10px;
  }
}
</style>