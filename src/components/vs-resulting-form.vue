
<template>
  <div>
    <div class="vs-preview-wrap vs-work__block">


    </div>
  </div>
</template>

<script>


export default {
  name: "vs-resulting-form",
  props: {
    options : {
      type: Object
    }

  },
  watch: {

  },
  data () {
    return {
      formParams: {
        ...this.options
      }
    }
  },
  computed: {

  },

}
</script>

<style lang="scss">
.vs-work__block{
  height: 100%;
  background: azure;
}


</style>