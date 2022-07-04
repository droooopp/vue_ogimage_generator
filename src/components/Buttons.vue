<template>
  <div class="btns">
    <div class="btns-container">
      <label for="file" class="btns-item -file">
        <span class="btns-ico">
          <font-awesome-icon
            icon="file-upload"
            size="3x"
            :style="{ color: 'white' }"
          />
        </span>
        <span class="btns-text">アップロード</span>
        <input
          v-on:change="fileChange"
          id="file"
          type="file"
          accept="image/*"
          class="btns-input"
        >
      </label>
      <div
        v-if="uploadedFlag"
        v-on:click="generate"
        class="btns-item -generate"
      >
        <span class="btns-ico">
          <font-awesome-icon
            icon="file-image"
            size="3x"
            :style="{ color: 'white' }"
          />
        </span>
        <span class="btns-text">画像を生成</span>
      </div>
      <a
        v-if="uploadedFlag && generatedFlag"
        :href="generatedImage"
        class="btns-item -download"
        download
      >
        <span class="btns-ico">
          <font-awesome-icon
            icon="file-download"
            size="3x"
            :style="{ color: 'white' }"
          />
        </span>
        <span class="btns-text">ダウンロード</span>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    'uploadedFlag',
    'generatedFlag',
    'fileChange',
    'generate',
    'generatedImage'
  ]
}
</script>

<style scoped>
.btns {
  max-width: 500px;
  margin: 30px auto 0;
}

.btns-container {
  display: flex;
}

.btns-item {
  position: relative;
  display: block;
  width: 80px;
  margin: auto;
  cursor: pointer;
  transition: all .6s;
}

.btns-item:hover {
  opacity: .3;
  cursor: pointer;
}

.btns-ico {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 80px;
  height: 80px;
  border-radius: 50%;
}

.btns-item.-file .btns-ico {
  background-color: #ff0000;
}

.btns-item.-generate .btns-ico {
  background-color: #005cff;
}

.btns-item.-download .btns-ico {
  background-color: #08bc15;
}

.btns-text {
  font-size: 13px;
  display: block;
  padding: 10px 0 0;
}

.btns-input {
  display: none;
}

a {
  color: #1d1d1d;
  text-decoration: none;
}
</style>
