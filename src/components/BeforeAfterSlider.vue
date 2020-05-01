<template>
  <div
    :style="{
      width: '1050px',
      height: '650px',
      background: getBackgroundUrl(after),
    }"
    class="bottom-layer"
  >
    <div
      :style="{
        width: sliderValue + '%',
        height: '100%',
        background: getBackgroundUrl(before),
      }"
      class="top-layer"
    />
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
      sliderValue: 60
    }
  },

  methods: {
    getBackgroundUrl( src ) {
      return `url('${src}')`;
    },
  },
};
</script>

<style>
.slider {
  width: 100%;
  padding: 0;
  position: absolute;
  bottom: calc(50% - 10px);
}

.slider .range-slider-rail, .slider .range-slider-fill {
    opacity: 0;
}

.bottom-layer {
  position: relative;
}

.top-layer {
  border-right: 2px solid #ddd;
}
</style>