<template>
    <div class="vs__browser-nav">
      <div
          v-for="(item, index) in allTabs"
          :key="index"
          :class="{'active-tab': item.id === activeTab.id}"
          class="vs__browser-item">
        <span class="vs__tab-name">
             {{ item.name1}}
        </span>
        <span
            @click="$emit('closeTab', item)"
            class="vs__tab-close">
          X
        </span>

      </div>
    </div>
</template>

<script>
export default {
name: "vs-browser-tabs",
  props: {
    activeTab: [String, Number, Object],
    allTabs: Array
  }
}
</script>

<style lang="scss">
.vs__browser-nav{
  display: flex;
}
.vs__browser-item{
  align-items: center;
  padding: 6px 12px;
  background: rgba(lightslategray, 0.8);
  &.active-tab{
    font-style: italic;
    //font-size: 12px;
    position: relative;
    background: lightslategray;
    &:after{
      position: absolute;
      bottom: 0px;
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