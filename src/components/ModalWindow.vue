<template>
  <div class="main">
    <h1 class="title">{{title}}</h1>
    <div class="container-folder">
      <GoldFolderTree v-for="fold in folderTree" :key="fold.id" :fold="fold" />
    </div>
  </div>
</template>

<script>

import GoldFolderTree from '@/components/GoldFolderTree.vue'

export default {
  name: 'ModalWindow',
  components: {
    GoldFolderTree
  },
  props: {
    title: String,
    folderTree: Array
  },
}
</script>

<style scoped lang="scss">
  .main {
    max-width: 400px;
    height: auto;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    border: 1px solid #42b983;
    margin: 0 auto;
    border-radius: 10px;
    color: white;
    background-color: white;
  }

  .title {
    padding: 10px;
    margin: 0 auto;
    background-color: #42b983;
    font-size: 26px;
    border-radius: 10px 10px 0 0;
  }
  .container-folder {
    padding: 10px 20px;
  }
  </style>