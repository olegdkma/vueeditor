<template>
  <div class="vs-webeditor">
    <vs-webeditor
        :openTabs="openFiles"
        :activeFile="activeTab"
        v-on:closeTab="closeTab"
        class="vs-main-panel"/>
    <vs-webeditor-aside
        :filesList="allFiles"
        v-on:selectedFile="reciveFileData"
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
      allFiles: [{name1: 'Index.vue', name2: 'asdas', id: 1}, {name1: 'vs-form.vue', name2: 'asdas', id:2}, {name1: 'vs-playground.vue', name2: 'asdas', id:3}],
      openFiles: [],
      activeTab: {},
    }
  },
  mounted() {
    //temporary
    this.openFiles = [this.allFiles[0]]
    this.activeTab= this.allFiles[0]
  },
  methods: {
    reciveFileData (value) {
      this.activeTab = value
      !this.openFiles.includes(value) ?  this.openFiles = [...this.openFiles, value] : false
      console.log(this.openFiles, this.activeTab)


    },
    closeTab(val){
      this.openFiles = this.openFiles.filter(el=> el.id !== val.id)
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
