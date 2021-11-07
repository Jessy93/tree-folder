<template>
  <div v-if="fold">
    <div  class="parent">
      <span class="folder"
        v-if="hasChildren" 
        :class="toggleChildrenIcon"
        @click="toggleChildren"
        @keypress="toggleChildren">
      </span>
      <span v-else class="no-folder">
        a
      </span>
      <h2 class="title title-2">{{fold.name}}</h2>
    </div>
    <div v-if="hasChildren" v-show="showChildren" class="children">
      <GoldFolderTree
        v-for="child in fold.children"
        :key="child.id"
        :fold="child"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'GoldFolderTree',
  props: {
    fold: {
      type: Object,
      required: true
    },
    folderTree: Array
  },
  data: () => ({
    showChildren: false,
  }),
  computed: {
    nodeMargin() {
      return {
        'margin-left': `${this.spacing}px`
      }
    },
    hasChildren() {
      const { children } = this.fold
      return children && children.length > 0
    },
    toggleChildrenIcon() {
      return this.showChildren ? 'fas fa-angle-down' : 'fas fa-angle-right'
    }
  },
  methods: {
    toggleChildren() {
      this.showChildren = !this.showChildren
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .parent {
    display: flex;
    align-items: center;
  }
  .title.title-2 {
    color: #639;
    margin: 5px 0 0 5px;
    font-size: 18px;
    line-height: 22px;
  }
  span {
    width: 10px;
    height: 10px;
    border-radius: 50px;
    border: 1px solid rebeccapurple;
    background-color: yellowgreen;
  }
  span.no-folder {
    background-color: red;
  }
  .children {
    margin-left: 10px;
  }
</style>
