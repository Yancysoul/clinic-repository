<template>
  <div class="groupHeader">
    <el-button type="danger" :size="size">删除</el-button>
    <el-button type="primary" :size="size" @click="add">新增</el-button>
    <div class="query">
      <el-input :size="size" placeholder="请输入搜索内容"></el-input>
    </div>
    <el-button type="success" :size="size">查询</el-button>
  </div>
</template>

<script>
export default {
  name: 'GroupHeader',
  data () {
    return {
      size: "mini"
    }
  },
  methods: {
    add () {
      this.$store.dispatch('SetGroupDialog', true)
      this.$store.dispatch('SetGroupForm', {})
      this.$store.dispatch('SetGroupTitle', '新增科室')
    }
  }
}
</script>

<style scoped lang='scss'>
.groupHeader {
  display: flex;
  align-items: center;
  .query {
    width: 250px;
    margin: 0 10px;
  }
}
</style>