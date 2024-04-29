<template>
  <div>
    <ul></ul>
    <li v-for="item in fileList">{{ item.name }}</li>
  </div>
  <!-- :on-exceed="handleExceed" -->
  <!-- limit="1" -->
  <el-upload
    v-model:file-list="fileList"
    class="upload-demo"
    drag
    action="https://run.mocky.io/v3/9d059bf9-4660-45f2-925d-ce80ad6c4d15"
    :multiple="true"
    :auto-upload="false"
    :on-exceed="handleExceed"
    limit="3"
  >
    <el-icon class="el-icon--upload"><upload-filled /></el-icon>
    <div class="el-upload__text">
      Drop file here or <em>click to upload</em>
    </div>
    <template #tip>
      <div class="el-upload__tip">
        jpg/png files with a size less than 500kb
      </div>
    </template>
  </el-upload>
</template>

<script setup lang="ts">
import type { UploadProps, UploadUserFile } from 'element-plus'
import { ref } from 'vue'
import { UploadFilled } from '@element-plus/icons-vue'

const fileList = ref<UploadUserFile[]>([
  {
    name: 'element-plus-logo.svg',
    url: 'https://element-plus.org/images/element-plus-logo.svg',
  },
  {
    name: 'element-plus-logo2.svg',
    url: 'https://element-plus.org/images/element-plus-logo.svg',
  },
])

const handleExceed: UploadProps['onExceed'] = (files, uploadFiles) => {
  console.log(files, uploadFiles)
}
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
