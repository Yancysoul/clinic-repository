<template>
  <div class="tableInfo">
    <el-breadcrumb separator-class="el-icon-arrow-right">
      <el-breadcrumb-item v-for="breadcrumb in breadcrumbList" :key="breadcrumb">{{ breadcrumb }}</el-breadcrumb-item>
    </el-breadcrumb>
    <div class="tableSearch">
      <div class="search">
        <input type="text" size="24" placeholder="请输入搜索内容">
        <i class="iconfont">&#xe614;</i>
      </div>
      <div class="search-span">
        <span v-for="word in searchWord" :key="word" :class="word === wordCur ? 'spanHover' : ''" @click="spanClick(word)">{{ word }}</span>
      </div>
    </div>
    <div class="container">
      <el-table
        :data="tableData"
        stripe
        :highlight-current-row="highlightCurrentRow"
        :header-cell-style="{background:'#f5f5f5'}"
        height="100%">
        <el-table-column
          prop="type"
          label="类型"
          min-width="10%">
        </el-table-column>
        <el-table-column
          prop="sort"
          label="类别"
          min-width="10%">
        </el-table-column>
        <el-table-column
          prop="num"
          label="编码"
          min-width="15%">
        </el-table-column>
        <el-table-column
          label="名称"
          min-width="20%">
          <template slot-scope="{ row }">
            <span @click="viewDetail" title="查看详情">{{ row.name }}</span>
          </template>
        </el-table-column>
        <el-table-column
          prop="detail"
          label="详细信息"
          min-width="25%">
        </el-table-column>
        <el-table-column
          min-width="20%">
          <template>
            <el-badge :value="120000" :max="999" class="item">
              <el-button size="mini" type="primary">评论</el-button>
            </el-badge>
            <el-badge :value="3" :max="999" class="item">
              <el-button size="mini" type="warning">收藏</el-button>
            </el-badge>
            <el-badge :value="3" :max="999" class="item">
              <el-button size="mini" type="success">浏览</el-button>
            </el-badge>
          </template>
        </el-table-column>
      </el-table>
    </div>
    <item-detail :dialogVisible="dialogVisible"></item-detail>
  </div>
</template>

<script>
import ItemDetail from '@/components/ItemDetail'
export default {
  name: 'TableInfo',
  components: { ItemDetail },
  data () {
    return {
      size: 'mini',
      highlightCurrentRow: true,
      dialogVisible: false,
      wordCur: '',
      searchWord: ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
    }
  },
  props: {
    breadcrumbList: Array,
    tableData: Array
  },
  methods: {
    viewDetail () {
      this.dialogVisible = true
    },
    spanClick (word) {
      this.wordCur = word
    },
    closeDialog () {
      this.dialogVisible = false
    }
  }
}
</script>

<style scoped lang="scss">
.tableInfo {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  padding: 20px 0;
  .tableSearch {
    width: 100%;
    flex-shrink: 0;
    display: flex;
    align-items: center;
    padding-left: 10px;
    flex-wrap: wrap;
    .search {
      margin-top: 5px;
      border: 1px solid #f1f1f1;
      border-radius: 10px;
      padding: 2px 10px;
      color: #333;
      input {
        border: 0 none;
        outline: none;
        font-size: 12px;
        margin-right: 10px;
      }
      i {
        font-size: 14px;
        cursor: pointer;
      }
    }
    .search-span {
      margin-top: 5px;
      // width: 100%;
      display: flex;
      flex-wrap: wrap;
      span {
        margin: 0 5px;
        cursor: pointer;
        color: #888;
        padding: 1px 2px;
        transition: all 0.3s;
        &:hover {
          text-decoration: underline;
          color: #fff;
          background-color: #409eff;
        }
      }
      .spanHover {
        color: #fff;
        background-color: #409eff;
      }
    }
  }
  .container {
    height: 100%;
    width: 100%;
    margin-top: 10px;
    position: relative;
    .el-table {
      position: absolute;
      left: 0;
      top: 0;
      border: 1px solid #EBEEF5;
      width: 100%;
      .item {
        margin-top: 8px;
        margin-right: 30px;
      }
    }
    span {
      cursor: pointer;
      &:hover {
        color: #409eff;
      }
    }
  }
}
</style>