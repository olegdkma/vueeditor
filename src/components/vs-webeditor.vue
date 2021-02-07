<template>
  <div class="vs-work-area">
    <vs-browser-tabs
        v-on:closeTab="closeTab"
        :activeTab="activeFile" :allTabs="openTabs"/>
<!--    <div class="vs-navs__block">
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

    </div>-->
    <div class="vs-work-area__body">
      <p>{{ activeFile }}</p>
      <vs-resulting-form/>

    </div>
  </div>
</template>

<script>
import VsResultingForm from "@/components/vs-resulting-form";
import VsBrowserTabs from "@/utils/vs-browser-tabs";
export default {
name: "vs-webeditor",
  components: {VsBrowserTabs, VsResultingForm},
  props:{
    openTabs:{
      type: Array
    },
    activeFile: {
      type: Object
    },
    activeTab: Object
  },
  data() {
    return {
      //activeTab: 0,
      tabs: []
    }
  },
  watch : {
    openTabs: {
      immediate: true,
      handler() {

      }
    },
    activeFile: {
      immediate: true,
      handler() {

      }
    }
  },
  methods: {
    closeTab (val) {
      this.$emit('closeTab', val)
    }
  }
}
</script>

<style lang="scss">
  .vs-work-area__body{
    display: flex;
    padding: 30px;

  }

</style>