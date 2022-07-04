<template>
  <div id="app">
    <Heading />
    <Preview
      :uploadedFlag="uploadedFlag"
      :generatedFlag="generatedFlag"
      :uploadedImage="uploadedImage"
    />
    <Result
      :uploadedFlag="uploadedFlag"
      :generatedFlag="generatedFlag"
    />
    <Buttons
      :uploadedFlag="uploadedFlag"
      :generatedFlag="generatedFlag"
      :fileChange="fileChange"
      :generate="generate"
      :generatedImage="generatedImage"
    />
  </div>
</template>

<script>
import html2canvas from 'html2canvas'
import 'reset.css'
import Heading from './components/Heading.vue'
import Buttons from './components/Buttons.vue'
import Preview from './components/Preview.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: {
    Heading,
    Buttons,
    Preview,
    Result
  },
  data() {
    return {
      uploadedImage: '',
      generatedImage: '',
      uploadedFlag: false,
      generatedFlag: false
    };
  },
  methods: {
    fileChange(e) {
      const files = e.target.files || e.dataTransfer.files;
      this.createImage(files[0]);
      this.uploadedFlag = true
      this.generatedFlag = false
      this.generatedImage = ''
      const result = document.querySelector(".result-canvas")
      result.innerHTML = ''
    },
    createImage(file) {
      const reader = new FileReader()
      reader.onload = (e) => {
        this.uploadedImage = e.target.result
      }
      reader.readAsDataURL(file)
    },
    generate() {
      if(this.generatedImage !== '') {
        return
      }
      const result = document.querySelector(".result-canvas")
      const capture = document.querySelector(".capture-container")
      const option = {scale:2}
      html2canvas(capture,option).then(function(canvas) {
        result.innerHTML = ''
        result.appendChild(canvas)
        this.generatedFlag = true
        this.generatedImage = canvas.toDataURL()
      }.bind(this))
    }
  }
}
</script>

<style>
#app {
  font-family: "ヒラギノ角ゴPro W3", "Hiragino Kaku Gothic Pro", "Yu Gothic Medium", "游ゴシック Medium", YuGothic, 游ゴシック体, メイリオ, Meiryo, "Helvetica Neue", Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  text-align: center;
  color: rgb(29, 29, 29);
  background-color: rgb(243, 243, 243);
  min-height: calc(100vh - 60px);
  padding-bottom: 60px;
}
</style>
