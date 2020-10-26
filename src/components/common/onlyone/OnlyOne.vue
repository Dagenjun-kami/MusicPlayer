<template>
  <div class="onlyone">
    <TitleHeader name="独家放送"></TitleHeader>
    <MusicListItem v-for="(item,index) in onlylist" :key="index" :item="item" :wth="28">
      <div slot="music-btm">
        <div class="btm">
            <img src="~assets/img/playMusic/cover_play.png" />
      </div>
      </div>
      <div slot="music-t"></div>
    </MusicListItem>
  </div>
</template>

<script>
import TitleHeader from "components/common/titleheader/TitleHeader";
import MusicListItem from "components/common/musiclist/MusicListItem";
import { getOnlyList } from "network/home";
export default {
  name:'OnlyOne',
  components: {
    TitleHeader,
    MusicListItem,
  },
  data() {
    return {
      onlylist: {},
    };
  },
  methods: {
    //获取独家放送信息
    getOnlyList() {
      getOnlyList().then((res) => (this.onlylist = res.result));
    },
  },
  created() {
    this.getOnlyList();
  },
};
</script>

<style scoped>
.onlyone {
  width: 80%;
  margin: 0 auto;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
.btm {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 22%;
  /* 相对自身偏移 */
  transform: translate(-50%, -50%);
}
.btm img {
  width: 100%;
  opacity: 0;
  transform: scale(0.7);
  transition: all 0.5s;
}
.itemImg:hover .btm img {
  opacity: 1;
  transform: scale(1);
}
</style>