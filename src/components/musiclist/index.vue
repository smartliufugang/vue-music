// 歌单详情列表
<template lang="pug">
  .music-list(@click="saveAddPlay(index)")
    .music-index
      span.index(v-if="!isPlaying") {{index + 1}}
      i.icon-menu(v-else)
    .music-info
      .music-detail
        .name {{name}}
        .singer {{getSinger}}
      .music-conf
        .mv.icon-menu
        .set.icon-menu
</template>
<script>
export default {
  props: {
    // 音乐的id
    id: {
      type: Number,
      default: 0
    },

    // 音乐的封面
    index: {
      type: Number,
      default: 0
    },

    // 音乐名称
    name: {
      type: String,
      default: ''
    },

    // 歌手
    singer: {
      type: Array,
      default: function () {
        return []
      }
    },

    // 返回对应的list的所有的数据
    list: {
      type: Object,
      default: function () {
        return {}
      }
    }
  },

  methods: {
    // 提示播放的音乐
    saveAddPlay (index) {
      this.$emit('play', index)
    }
  },

  computed: {
    getSinger () {
      return this.singer.map(item => item.name).toString()
    },

    isPlaying () {
      return false
    }
  },
  created () {
    // console.log(this.singer.map(item => item.name).toString())
  }
}
</script>

<style lang="scss" scoped>
.music-list{
  width: 100%;
  height: auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: p2r(0.1rem) 0;
  position: relative;
  @include border-1px();
  .music-index{
    flex:0 0 p2r(0.9rem);
    margin-right: p2r(0.1rem);
    display: flex;
    align-items: center;
    justify-content: center;
    i{
      font-size: $f_small_m;
      color: $primary_color;
    }
    span{
      font-size: $f_small_m;
      color: $color_gray;
    }
  }
  .music-info{
    flex:1 1 auto;
    overflow: hidden;
    display: flex;
    align-items: center;
    .music-detail{
      flex:1 1 auto;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: flex-start;
      overflow: hidden;
      .name{
        font-size: $f_small_l;
        color: $text_color;
        @include els();
        width: 100%;
        text-align: left;
      }
      .singer{
        width: 100%;
        text-align: left;
        font-size: $f_small_s;
        color: $color_gray;
        @include els();
      }
    }
    .music-conf{
      flex:0 0 p2r(1.3rem);
      display: flex;
      align-items: center;
      color: $color_gray_slow;
      font-size: $f_small_m;
      height: p2r(0.6rem);
      .mv,.set{
        flex: 0 0 p2r(0.6rem);
        display: flex;
        align-items: center;
        justify-content: center;
      }
      .set{
        margin-left: p2r(0.1rem);
      }
    }
  }

}
</style>
