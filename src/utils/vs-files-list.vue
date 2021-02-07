<template>
  <div

      class="vs__files-tree">
      <span
          v-for="(item,index) in allFiles"
          @click="$emit('selectedFile', item)"
          :key="index"
          class="vs__file-item">
          {{ item.name1 }}
      </span>
  </div>
</template>

<script>
export default {
  name: "vs-files-list",
  props: {
    allFiles: Array
  }
}
</script>

<style lang="scss">
  .vs__file-item{
    padding: 8px 15px;
    font-size: 12px;
    display: flex;
    align-items: center;
    cursor: pointer;
    &:hover, &.active{
      background: #242424;
    }
  }
</style>