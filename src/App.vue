<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" @click="show = true">
    <HelloWorld msg="Welcome to Your Vue.js App" @click="title = 'Hello World'"/>
    <!-- <JsonEditorVue /> -->
    <!-- <AsImage :title="title"></AsImage> -->
    <AsImage
      class="image"
      :width="2111"
      :height="1074"
      :src="'//d3skwsdk169y0b.cloudfront.net/image/dress.jpg'"
      :lazy="true"
      :duration="2"
      :quantity="90"
      format="png"
      :auto-webp="true"
      :progressive="false"
      :responsive="true"
      :image-provider="useFpProvider"
    >
      <template #loading>
        <div class="placeholder">
          Loading
        </div>
      </template>

      <template
        #webglFilter="{
          image
        }"
      >
        <Fake3d :image="image" depth="//d3skwsdk169y0b.cloudfront.net/image/dress-depth.jpg" />
      </template>
    </AsImage>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
// import AsImage from 'universal-vue-test'
// import 'universal-vue-test/dist/style.css'
import AsImage from '@vue-awesome-image/as-image'
import '@vue-awesome-image/as-image/dist/style.css'
import Fake3d from '@vue-awesome-image/filter-fake3d'
import { useFpProvider } from '@vue-awesome-image/providers'
export default {
  name: 'App',
  components: {
    HelloWorld,
    // SketchRule
    AsImage,
    Fake3d,
  },
  data () {
    return {
      title: 'asdf',
      show: false,
      useFpProvider,
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

</style>
