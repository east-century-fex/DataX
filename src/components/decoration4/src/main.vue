<template>
  <div class="dv-decoration-4" :ref="ref">
    <div
      :class="`container ${reverse ? 'reverse' : 'normal'}`"
      :style="reverse ? `width:${width}px;height:5px` : `width:5px;height:${height}px;`"
    >
      <svg :width="reverse ? width : 5" :height="reverse ? 5 : height">
        <polyline
          stroke="rgba(255, 255, 255, 0.3)"
          :points="reverse ? `0, 2.5 ${width}, 2.5` : `2.5, 0 2.5, ${height}`"
        />
        <polyline
          class="bold-line"
          stroke="rgba(255, 255, 255, 0.3)"
          stroke-width="3"
          stroke-dasharray="20, 80"
          stroke-dashoffset="-30"
          :points="reverse ? `0, 2.5 ${width}, 2.5` : `2.5, 0 2.5, ${height}`"
        />
      </svg>
    </div>
  </div>
</template>

<script>
import autoResize from '../../../mixin/autoResize'

export default {
  name: 'DvDecoration4',
  mixins: [autoResize],
  props: ['reverse'],
  data () {
    return {
      ref: 'decoration-4'
    }
  }
}
</script>

<style lang="less">
.dv-decoration-4 {
  position: relative;
  width: 100%;
  height: 100%;

  .container {
    display: flex;
    overflow: hidden;
    position: absolute;
  }

  .normal {
    height: 0% !important;
    animation: ani-height 3s ease-in-out infinite;
    left: 50%;
    margin-left: -2px;
  }

  .reverse {
    width: 0% !important;
    animation: ani-width 3s ease-in-out infinite;
    top: 50%;
    margin-top: -2px;
  }

  @keyframes ani-height {
    70% {
      height: 100%;
    }

    100% {
      height: 100%;
    }
  }

  @keyframes ani-width {
    70% {
      width: 100%;
    }

    100% {
      width: 100%;
    }
  }
}
</style>
