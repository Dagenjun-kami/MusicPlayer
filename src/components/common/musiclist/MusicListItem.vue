<template>
  <div class="musiclistitem" @click="toListPage(item.id)" :style="{width:wth+'%'}">
    <el-card :body-style="{ padding: '0px',width:'100%' }" shadow="hover"> 
      <img :src="item.coverImgUrl || item.sPicUrl || item.cover" class="image" />
      <div class="cover"></div>
      <slot name="music-t">
        <div class="right-t">
          <i class="el-icon-headset" style="paddingTop: 4px;paddingLeft:15px"></i>
          <span>{{item.playCount >= 10000 ? (item.playCount/10000).toFixed(0)+'万' : item.playCount}}</span>
        </div>
      </slot>
      <div class="btm">
        <img src="~assets/img/playMusic/cover_play.png">
      </div>
      <div class="user" v-if="userShow">
        <span><i class="el-icon-user"></i>{{item.artistName || item.creator.nickname}}</span>
      </div>
    </el-card>
    <div class="namet">
      <span>{{item.name}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name:'MusicListItem',
  data() {
    return {
    };
  },
  props: {
    item: {
      type: Object,
      default() {
        return {};
      },
    },
    wth:{
      type:Number,
      default:18
    },
    topShow:{
      type:Boolean,
      default:true,
    },
    userShow:{
      type:Boolean,
      default:false,
    },
    mvType:{
      type:Boolean,
      default:false,
    }
  },
  created() {
    // console.log(this.item);
  },
  methods: {
    // 因为视频也用了该组件 所以需要判断
    toListPage(id) {
      if(this.mvType){
        this.$router.push('/mvvideo' + id);
        return;
      }
      this.$router.push('/songs' + id);
      console.log('/songs' + id);
    },
  },
};
</script>

<style scped>
.user{
  width: 100%;
  position: absolute;
  bottom: 50px;
  left: 0;
  font-size: 13px;
  color: aliceblue;
  background-image: linear-gradient(rgba(0,0,0,0.02), rgba(0,0,0,0.4));
}
.namet {
  padding-top: 10px;
  font-size: 13px;
  height: 40px;
}

.btm {
  position: absolute;
  top:23%;
  left:30%;
  cursor: pointer;
  transition: opacity 0.3s;
  opacity: 0;
}

.musiclistitem:hover .btm {
  opacity: 1;
}

.right-t {
  width: 80px;
  height: 14px;
  position: absolute;
  padding-top: 1px;
  top: 0px;
  right: 1px;
  font-size: 12px;
  background-image: linear-gradient(
    to left,
    rgba(0, 0, 0, 0.6),
    rgba(0, 0, 0, 0)
  );
  color: #fff;
  display: flex;
  justify-content: space-evenly;
}
.musiclistitem {
  margin-top: 25px;
  position: relative;
  overflow: hidden;
  cursor: pointer;
  margin-bottom: 10px;
  line-height: 1.5;
  /* min-height: 250px; */
}
.time {
  font-size: 13px;
  color: #999;
}
.bottom {
  margin-top: 13px;
  line-height: 12px;
}

.button {
  padding: 0;
  float: right;
}

.image {
  width: 100%;
  display: block;
  transition: transform 0.7s;
}
.musiclistitem:hover .image{
    transform: scale(1.1);
}
.cover {
    opacity: 0;
    transition: opacity .6s;
    width: 100%;
    height: 75.5%;
    left: 0;
    right: 0;
    bottom: 0;
    top: 0;
    position: absolute;
    background-color: rgba(0,0,0,.2);
    color: white;
}
.musiclistitem:hover .cover {
    opacity: 1;
}
.clearfix:before,
.clearfix:after {
  display: table;
  content: "";
}

.clearfix:after {
  clear: both;
}
</style>