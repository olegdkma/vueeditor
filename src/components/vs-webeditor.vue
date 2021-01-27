<template>
  <div class="vs-work-area">
    <div class="vs-navs__block">
  <div
          v-for="(item, index) in allTabs"
          :key="index"
          :class="{ 'active': index === 0 }"
          class="vs-navs">
          <span>
            {{ item.name1 }}
          </span>

            <span
                @click="closeTab"
                class="vs-navs__close">X</span>
      </div>

    </div>
    <div class="vs-work-area__body">
      <p>{{ activeFile }}</p>
      <vs-resulting-form/>

    </div>
  </div>
</template>

<script>
import VsResultingForm from "@/components/vs-resulting-form";
export default {
name: "vs-webeditor",
  components: {VsResultingForm},
  props:{
    openTabs:{
      type: Array
    },
    activeFile: {
      type: Object
    }
  },
  data() {
    return {
      activeTab: this.activeFile,
      allTabs: [...this.openTabs]
    }
  },
  watch : {
    openTabs: {
      immediate: true,
      handler() {
        this.allTabs = [...this.openTabs]
      }
    },
    activeFile: {
      immediate: true,
      handler() {
        this.activeTab = this.activeFile
      }
    }
  },
  methods: {
    closeTab () {
      console.log('removeTab')
    }
  }
}
</script>

<style lang="scss">
  .vs-work-area__body{
    display: flex;
    padding: 30px;

  }
  .vs-navs{
    align-items: center;
    &.active{
     font-style: italic;
      font-size: 12px;
      position: relative;
      &:after{
        position: absolute;
        bottom: -1px;
        content: '';
        width: 100%;
        right: 0;
        height: 2px;
        background: aquamarine;
      }
    }
    &__close{
      font-style: normal;
    }
  }
</style>