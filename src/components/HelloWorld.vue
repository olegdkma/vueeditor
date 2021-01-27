<template>
  <div class="vs-webeditor">
    <vs-webeditor
        :openTabs="openFiles"
        :activeFile="activeTab"
        class="vs-main-panel"/>
    <vs-webeditor-aside
        :filesList="allFiles"
        v-on:chooseFile="reciveFileData"
        class="vs-aside-panel"/>
  </div>
</template>

<script>
import VsWebeditor from "./vs-webeditor";
import VsWebeditorAside from "@/components/vs-webeditor-aside";
export default {
  name: 'HelloWorld',
  components: {VsWebeditorAside, VsWebeditor},
  props: {

  },
  data() {
    return {
      allFiles: [{name1: 'Index.vue', name2: 'asdas'}, {name1: 'v-form.vue', name2: 'asdas'}],
      openFiles: [{name1: 'Index.vue', name2: 'asdas'}],
      activeTab: {name1: 'Index.vue', name2: 'asdas'}
    }
  },
  methods: {
    reciveFileData (value) {
      this.activeTab = value
      !this.openFiles.includes(value) ?  this.openFiles = [...this.openFiles, value] : false
      console.log(this.openFiles, this.activeTab)


    }
  }

}
</script>


<style lang="scss">
  $primary: #151515;
  $secondary: #242424;
  .vs-webeditor{
    display: flex;
  }
  .vs-aside-panel{
    width: 25%;
    flex-shrink: 0;
    background: $primary;
    height: 100vh;
    border: 1px solid $secondary;
  }
  .vs-main-panel {
    width: 75%;
    background: $primary;
  }
</style>
