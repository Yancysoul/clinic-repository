<template>
  <div class="treeInfo">
    <el-scrollbar>
      <el-collapse @change="changeCollapse" accordion v-model="curCol" v-if="treeData">
        <el-collapse-item v-for="(data, index) in treeData" :key="index" :title="data.fname" :name="data.fdiseaseTypeID">
          <el-row>
            <el-col :md="24" :lg="12" :xl="8" v-for="(item, index) in data.childrens" :key="index"><div :class="treeFlag === item.fdiseaseTypeID ? 'treeHover' : ''" @click="treeClick(data.fname, item.fname, item.fdiseaseTypeID)">{{ item.fname }}</div></el-col>
          </el-row>
        </el-collapse-item>
      </el-collapse>
    </el-scrollbar>
  </div>
</template>

<script>
export default {
  name: 'TreeInfo',
  data () {
    return {
      treeFlag: 9,
      curCol: 1
    }
  },
  props: {
    treeData: Array,
    treeItemData: Array
  },
  methods: {
    handleNodeClick (data) {
      
    },
    treeClick (title, item, id) {
      this.$parent.setBreadcrumbList([title, item])
      this.$parent.setFDiseaseTypeID(id)
      this.treeFlag = id
    },
    changeCollapse (val) {

    }
  }
}
</script>

<style scoped lang="scss">
.treeInfo {
  height: 100%;
  padding: 20px;
  width: 15%;
  min-width: 200px;
  .el-scrollbar {
    height: 100%;
  }
  .el-row {
    // background-color: #f0f3f8;
    .el-col {
      font-size: 12px;
      div {
        height: 30px;
        line-height: 28px;
        text-align: center;
        padding: 0 4px;
        border: 1px solid #409eff;
        color: #409eff;
        margin: 5px 2px;
        overflow: hidden;
        text-overflow:ellipsis;
        white-space: nowrap;
        border-radius: 5px;
        cursor: pointer;
        transition: all 0.3s;
        &:hover {
          background-color: #409eff;
          color: #fff;
        }
      }
      .treeHover {
        color: #fff;
        background-color: #409eff;
      }
    }
  }
}
</style>
<style>
.el-collapse-item__header {
  /* background-color: #f0f3f8!important; */
  font-size: 14px;
  padding-left: 20px;
  padding-right: 10px;
}
.el-collapse-item__content {
  padding-bottom: 0!important;
}
.treeInfo .el-scrollbar__wrap {
  overflow-x: hidden;
}
</style>