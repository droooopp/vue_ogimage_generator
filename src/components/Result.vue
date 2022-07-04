<template>
  <div class="result">
    <h2
      v-if="uploadedFlag && generatedFlag"
      class="result-heading"
    >生成結果</h2>
    <div class="result-canvas"></div>
  </div>
</template>

<script>
export default {
  props: [
    'uploadedFlag',
    'generatedFlag'
  ]
}
</script>

<style scoped>
.result {
  width: 600px;
  margin: 50px auto 0;
}

.result-heading {
  padding: 15px 50px;
  width: 100px;
  font-size: 16px;
  background-color: #fff;
  font-weight: 700;
  display: inline-block;
  border: 1px solid #1d1d1d;
  border-radius: 25px;
}

.result-canvas {
  margin: 30px auto;
}
</style>
