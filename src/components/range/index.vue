<template>
  <div class="vux-range-input-box" style="width:180px;position:relative;margin-right:20px;">
    <input class="vux-range-input" v-model="value">
  </div>
</template>

<script>
  const Powerange = require('./powerange')
  export default {
    props: {
      decimal: {
        type: Boolean,
        default: false
      },
      value: {
        default: 0,
        twoWay: true
      },
      min: {
        default: 0
      },
      minHTML: String,
      maxHTML: String,
      max: {
        default: 100
      },
      step: {
        default: 0
      },
      disabled: {
        type: Boolean,
        default: false
      },
      disabledOpacity: {
        default: 0.75
      },
      rangeBarHeight: {
        type: Number,
        default: 1
      },
      rangeHandleHeight: {
        type: Number,
        default: 30
      }
    },
    ready () {
      const _this = this
      let options = {
        decimal: _this.decimal,
        start: _this.value,
        min: _this.min,
        max: _this.max,
        minHTML: _this.minHTML,
        maxHTML: _this.maxHTML,
        disable: _this.disabled,
        disabledOpacity: _this.disabledOpacity,
        callback: function () {

        }
      }
      if (_this.step !== 0) {
        options.step = _this.step
      }
      this.range = new Powerange(this.$el.querySelector('.vux-range-input'), options)
      const handleTop = (this.rangeHandleHeight - this.rangeBarHeight) / 2
      this.$el.querySelector('.range-handle').style.top = `-${handleTop}px`
      this.$el.querySelector('.range-bar').style.height = `${this.rangeBarHeight}px`
    },
    beforeDestroy () {
      // @todo
    }
  }
</script>

<style>
@import './powerange.css'
</style>