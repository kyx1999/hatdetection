<template>
  <video-player
    ref="videoPlayer"
    class="video-player vjs-custom-skin"
    :playsinline="true"
    :options="playerOptions"
    @play="onPlayerPlay($event)"
    @pause="onPlayerPause($event)"
    @ended="onPlayerEnded($event)"
  />
</template>

<script>
export default {
  name: 'RTMPPlayer',
  props: {
    state: Boolean,
    videoUrl: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      playerOptions: {
        playbackRates: [0.7, 1.0, 1.5, 2.0], // 播放速度
        autoplay: true, // 如果true,浏览器准备好时开始回放。
        muted: false, // 默认情况下将会消除任何音频。
        loop: true, // 导致视频一结束就重新开始。
        preload: 'auto', // 建议浏览器在<video>加载元素后是否应该开始下载视频数据。auto浏览器选择最佳行为,立即开始加载视频（如果浏览器支持）
        language: 'zh-CN',
        aspectRatio: '16:9', // 将播放器置于流畅模式，并在计算播放器的动态大小时使用该值。值应该代表一个比例 - 用冒号分隔的两个数字（例如"16:9"或"4:3"）
        fluid: true, // 当true时，Video.js player将拥有流体大小。换句话说，它将按比例缩放以适应其容器。
        sources: [{
          type: 'rtmp/flv', // 这里的种类支持很多种：基本视频格式、直播、流媒体等，具体可以参看git网址项目
          src: 'rtmp://192.168.75.130:1935/live/kyx1999' // url地址
        }],
        // hls:true, //如果是播放m3u8必须加（需注释掉techOrder,不然会有报错）
        techOrder: ['flash'], // 播放rtmp必须加
        poster: '', // 你的封面地址
        notSupportedMessage: '此视频暂无法播放，请稍后再试', // 允许覆盖Video.js无法播放媒体源时显示的默认信息。
        controlBar: {
          timeDivider: true,
          durationDisplay: true,
          remainingTimeDisplay: false,
          fullscreenToggle: true // 全屏按钮
        }
      }
    }
  },
  computed: {
    player() {
      return this.$refs.videoPlayer.player
    }
  },
  watch: {
    videoUrl: function(val) {
      if (val !== '') {
        this.$refs.videoPlayer.player.src(val)
      }
    },
    state: function(val) {
      if (val) {
        this.$refs.videoPlayer.player.pause()
      }
    }
  },
  methods: {
    onPlayerPlay(player) {
      console.log('play')
    },
    onPlayerPause(player) {
      console.log('pause')
    },
    onPlayerEnded(player) {
      console.log('ended')
    }
  }
}
</script>
