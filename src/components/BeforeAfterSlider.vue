<template>
  <div 
    :style="{
      maxWidth: containerWidth,
    }"
    class="before-after-slider"
  >
    <div
      class="before-after-slider__layer --bottom"
    >
      <img
        ref="bottom-img"
        :src="after"
        class="before-after-slider__image --bottom"
        @load="resize"
      >
      <div
        :style="{
          width: sliderValue + '%',
        }"
        class="before-after-slider__layer --top"
      >
        <img
          :src="before"
          class="before-after-slider__image --top"
        >
      </div>
    </div>
    <range-slider
      class="slider"
      min="0"
      max="100"
      step="2"
      v-model="sliderValue">
    </range-slider>
  </div>
</template>

<script>
import RangeSlider from 'vue-range-slider'
import 'vue-range-slider/dist/vue-range-slider.css'

export default {

  components: {
    RangeSlider
  },

  props: {
    before: {
      type: String,
      required: true,
    },
    after: {
      type: String,
      required: true,
    },
  },

  data () {
    return {
      sliderValue: 60,
      containerWidth: '100%',
    }
  },

  methods: {
   resize() {
      this.containerWidth = this.$refs['bottom-img'].clientWidth + 'px';
   }
  },
};
</script>

<style lang="less">
.slider {
  width: 100%;
  padding: 0;
  position: absolute;
  bottom: calc(50% - 10px);

  .range-slider-rail {
    opacity: 0;
  }

  .range-slider-fill {
    opacity: 0;
  }
}

.before-after-slider {
  position: relative;

  &__layer {
    height: 100%;
    overflow: hidden;

    display: flex;
    align-items: center;

    background: #ccc;

    &.--bottom {
      position: relative;
    }

    &.--top {
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;

      border-right: 2px solid #ddd;
    }
  }

  &__image {
    &.--top {
      max-height: 100%;
    }

    &.--bottom {
      max-width: 100%;
    }
  }
}
</style>