<template>
  <div class="vs-navs-wrap">
    <div class="vs-navs__block">
      <div
          v-for="(item, index) in navs"
          :key="index"
          class="vs-navs">
        {{ item }}
      </div>
    </div>

    <div
        class="vs-settings__block">
        <div class="vs-settings__header">
          Files
        </div>
        <p
          v-for="(item,index) in filesData"
          :key="index"
          :class="{ 'active': index === 0 }"
          @click="$emit('chooseFile', item)"
          class="vs-settings__item"
        >
          <img
              class="vs-settings__file"
              src="https://cdn0.iconfinder.com/data/icons/file-format-3d-graphics-flat-filled/64/file_document_format_76-512.png" alt="">
          {{ item.name1 }}
        </p>
    </div>
  </div>

</template>

<script>
export default {
  name: "vs-webeditor-aside",
  props: {
    filesList: {
      type: Array,
    }
  },
  data() {
    return {
      filesData: [...this.filesList],
      navs: ['Files', 'Eslint', 'Git']
    }
  },
  computed :{
    activeCl(i) {
      return i === 0 ? 'active' : ''
    }
  },
}
</script>

<style lang="scss">
  .vs-navs__block{
    //padding: 0px 12px;
    display: flex;
    border: 1px solid #242424;
  }
  .vs-navs{
    font-size: 16px;
    font-weight: 700;
    padding: 10px;
    border-right: 1px solid #242424;
    min-width: 60px;
    cursor: pointer;
    text-align: center;
    display: flex;
    &__close{
      //font-weight: 900;
      cursor: pointer;
      margin-left: 10px;
      font-size: 10px;
    }
  }
  .vs-settings{
    &__header{
      padding: 8px 15px;
      font-size: 14px;
      //border-top: 1px solid #242424;
      border-bottom: 1px solid #242424;
    }
    &__item{
      padding: 8px 15px;
      font-size: 12px;
      display: flex;
      align-items: center;
      cursor: pointer;
      &:hover, &.active{
        background: #242424;
      }
    }
    &__file{
      height: 15px;
      margin-right: 5px;
    }
  }
</style>