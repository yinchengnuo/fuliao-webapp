<template>
  <div class="small-video-list-item" @click="toVideo" :style="{ background: 'url(' + videoInfo.cover + ') no-repeat center', backgroundSize: '32vw'}">
      <span class="hot" v-if="index === 0 || index === 1 || index === 2">热门</span>
      <div class="play-shadow">
        <Play class="play"></Play>
      </div>
      <div class="like-shadow">
        <Liked class="liked"></Liked>
         <span class="liked-num">{{videoInfo.like_num}}</span>
      </div>
  </div>
</template>

<script>
import Play from '../Public/IconFont/Play'
import Liked from '../Public/IconFont//Liked'
export default {
  name: 'SmallVideoListItem',
  props: ['videoInfo', 'index'],
  components: {
    Play,
    Liked
  },
  methods: {
    toVideo () {
      let name = ''
      if (this.$route.name === 'VideoOne') {
        name = 'VideoTwo'
      } else if (this.$route.name === 'VideoTwo') {
        name = 'VideoThr'
      } else if (this.$route.name === 'VideoThr') {
        name = 'VideoOne'
      } else if (this.$route.name === 'SmallVideoList') {
        name = 'VideoOne'
      }
      this.$router.push({
        name,
        params: { videoInfo: this.videoInfo }
      })
    }
  }
}
</script>

<style lang="less" scoped>
.small-video-list-item {
    width: 32vw;
    height: 44.22vw;
    margin: 0 0 1vw 1vw;
    float: left;
    position: relative;
    border-radius: 8px;
    .hot {
        .wrapper(@width: 10vw; @height: 4vw; @left: 2vw; @top: 2vw; );
        text-align: center;
        line-height: 4vw;
        border-radius: 8px;
        color: #fff;
        background: linear-gradient(315deg, rgb(255, 199, 117), rgb(255, 106, 0));
    }
    .play {
        .wrapper(@width: 8vw; @height: 8vw; @left: auto; @top: 2vw; @right: 2vw;);
        .iconfont(8vw);
        color: #fff;
    }
    .liked {
        .wrapper(@width: 4vw; @height: 4vw; @left: 2vw; @top: 2vw;);
        .iconfont(4vw);
        color: #fff;
    }
    .play-shadow {
      .wrapper(@height: 14vw;);
      border-radius: 8px;
      background: linear-gradient(rgba(0, 0, 0, .7), rgba(255, 255, 255, 0));
    }
    .like-shadow {
      .wrapper(@top: auto; @bottom: 0; @height: 8vw;);
      border-radius: 8px;
      background: linear-gradient(rgba(255, 255, 255, 0), rgba(0, 0, 0, .7));
    }
    .liked-num {
        .wrapper(@width: auto; @height: 4vw; @left: 6vw; @top: 2vw;);
        color: #fff;
    }
}
</style>
