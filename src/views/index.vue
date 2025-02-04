<script setup lang="ts">
  import type { UploadProps } from 'ant-design-vue'

  const fileList = ref<UploadProps['fileList']>([])
  const imgsUrl = computed(() => fileList.value ? fileList.value.map(file => URL.createObjectURL(file?.originFileObj)) : [])
</script>

<template>
  <div mb-10>
    <h1>ColoRadar</h1>
  </div>
  <div flex="~ col items-center" class="gap-4">
    <a-upload
      v-if="!fileList?.length"
      v-model:file-list="fileList"
      name="file"
      :multiple="false"
      accept="image/*"
      :show-upload-list="false"
    >
      <a-button>
        <div flex="~ items-center gap-2">
          <i i-carbon:image class="text-xl" />
          打开照片
        </div>
      </a-button>
    </a-upload>

    <TheImage v-else :imgs="imgsUrl" />
  </div>
</template>
