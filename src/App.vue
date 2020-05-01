<template>
  <div id="app">
    <before-after-slider 
      :before="require('@/assets/old.jpg')"
      :after="require('@/assets/new.jpg')"
    />
  </div>
</template>

<script>
import BeforeAfterSlider from './components/BeforeAfterSlider.vue'

export default {
  name: 'App',
  components: {
    BeforeAfterSlider,
  }
}
</script>

<style>
html, body, #app {
  width: 100%;
  height: 100%;
  margin: 0;
}
</style>