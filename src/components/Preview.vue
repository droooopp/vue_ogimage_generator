<template>
  <div
    v-if="uploadedFlag && !generatedFlag"
    class="preview"
  >
    <h2 class="preview-heading">プレビュー</h2>
    <div class="capture">
      <div class="capture-container">
        <div class="featurelogo">
          <img src="@/assets/logo.png">
        </div>
        <div class="thumb">
          <img :src="uploadedImage">
        </div>
        <div class="brandlogo">
          <img src="@/assets/header.png">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    'uploadedFlag',
    'generatedFlag',
    'uploadedImage'
  ]
}
</script>

<style scoped>
.preview {
  width: 600px;
  margin: 50px auto 0;
}

.preview-heading {
  padding: 15px 50px;
  width: 100px;
  font-size: 16px;
  background-color: #fff;
  font-weight: 700;
  display: inline-block;
  border: 1px solid #1d1d1d;
  border-radius: 25px;
}

.capture {
  margin: 30px 0 0;
  border: 1px solid #f3f3f3;
  display: inline-block;
}

.capture-container {
  display: flex;
  justify-content: center;
  margin: auto;
  width: 600px;
  height: 315px;
  background: #fff;
  box-sizing: border-box;
}

.featurelogo,
.brandlogo {
  width: 167.5px;
  display: flex;
}

.featurelogo img,
.brandlogo img {
  margin: auto;
  width: 100px;
}

.thumb {
  position: relative;
  margin: auto;
  width: 265px;
  height: 265px;
  overflow: hidden;
}

.thumb img {
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;
  min-width: 100%;
  max-width: 100%;
  height: auto;
}
</style>
