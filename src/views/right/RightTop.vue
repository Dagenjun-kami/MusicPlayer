<template>
  <div class="rt-top">
    <el-tabs v-model="activeName" @tab-click="handleClick" class="tabs">
      <el-tab-pane
        class="tabs-item"
        v-for="item in tabs"
        :key="item.name"
        :label="item.label"
        :name="item.name"
      ></el-tab-pane>
    </el-tabs>
    <!-- <button @click="handel">+++</button> -->
  </div>
</template>

<script>
export default {
  name:'righttop',

  data() {
    return {
      activeName: "/home/rtstyle",
      tabs: [
        { label: "个性推荐", name: "/home/rtstyle", },
        { label: "歌单", name: "/home/rtsongs" },
        { label: "主播电台", name: "/home/rtanchor" },
        { label: "排行榜", name: "/home/rtlist" },
        { label: "歌手", name: "/home/rtsinger" },
        { label: "最新音乐", name: "/home/rtnewsing" },
      ],
    };
  },

  methods: {
    handleClick(tab, event,name) {
        // console.log(tab, event);
      this.$router.replace(tab.name);
      this.activeName = tab.name;
    },

  },
};
</script>
<style >
.tabs .el-tabs__item {

  padding: 0 10px;
  text-align: center;
  border-radius: 5px;
  color: rgba(0, 0, 0, 0.5);
}
.el-tabs__active-bar {
    position: absolute;
    bottom: 0;
    left: 0;
    height: 2px;
    background-color: #536b83;
    z-index: 1;
    transition: transform .3s cubic-bezier(.645,.045,.355,1);
    list-style: none;
}
</style>
<style scoped>
.rt-top {
  width: 100%;
  text-align: center;
}
.tabs {
  display: flex;
  justify-content: center;
}
</style>