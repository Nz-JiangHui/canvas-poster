<template>
  <div>
    <img id="poster" class="save-poster" :src="imagesrc" />

    <canvas id="canvas" width="640" height="810"></canvas>
  </div>
</template>

<script>
export default {
  data () {
    return {
      imagesrc: ''
    }
  },
  methods: {
    genPoster () {
      var _this = this
      var oCanvas = document.querySelector('#canvas')

      var ctx = oCanvas.getContext('2d')

      ctx.fillRect(0, 0, 640, 810) // 指定画布大小
      var oImg = new Image()

      oImg.setAttribute('crossOrigin', 'anonymous')

      oImg.src = '/src/assets/logo.png'

      oImg.onload = function () {
        ctx.drawImage(oImg, 0, 0, 640, 810)
        var oImg1 = new Image()

        oImg1.setAttribute('crossOrigin', 'anonymous')

        oImg1.src = '/src/assets/logo.png'

        oImg1.onload = function () {
          ctx.drawImage(oImg1, 410, 410, 64, 81)
          ctx.font = '48px serif'
          ctx.textBaseline = 'hanging'
          ctx.strokeText('Hello world', 100, 100)
          _this.imagesrc = oCanvas.toDataURL()
        }
      }
    }
  },
  mounted () {
    this.genPoster()
  }
}
</script>

<style scoped>
#canvas{
  display: none;
}
</style>
