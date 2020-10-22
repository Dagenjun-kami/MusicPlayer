<template>
  <div class="main">
    <div id="app">
      <TopBar></TopBar>
      <CenterAll class="center-m"></CenterAll>
      <BottomBar class="btm-b"></BottomBar>
    </div>
  </div>
</template>

<script>
import TopBar from "components/common/topbar/TopBar";
import BottomBar from "components/common/bottombar/BottomBar";
import CenterAll from "views/center/CenterAll";

// import {get} from 'network/request'
export default {
  name: "APP",
  components: {
    TopBar,
    BottomBar,
    CenterAll,
  },
  data() {
    return {
    };
  },
};
</script>

<style  scoped>
.center-m {
  position: relative;
}
.btm-b {
  position: relative;
}
#app {
  min-width: 1200px;
  margin: 0 auto;
  height:100%;
  overflow: hidden;
  position: relative;
  background: #fff;
}

.main{
  position: relative;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

</style>
