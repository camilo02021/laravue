<template>
  <div class="components-container">
    <code>
      Based on <a class="link-type" href="https://github.com/rowanwins/vue-dropzone"> dropzone </a>.
      {{ $t('components.dropzoneTips') }}
    </code>
    <div class="editor-container">
      <dropzone id="myVueDropzone" url="https://httpbin.org/post" @dropzone-removedFile="dropzoneR" @dropzone-success="dropzoneS" />
    </div>
  </div>
</template>

<script>
import Dropzone from '@/components/Dropzone.vue';

export default {
  name: 'DropzoneDemo',
  components: { Dropzone },
  methods: {
    dropzoneS(file) {
      this.$message({ message: 'Upload success', type: 'success' });
    },
    dropzoneR(file) {
      this.$message({ message: 'Delete success', type: 'success' });
    },
  },
};
</script>

