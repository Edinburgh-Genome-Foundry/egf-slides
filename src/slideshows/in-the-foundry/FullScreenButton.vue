<template lang="pug">
.eg-fullscreen-button(@click='goFullScreen')
  slot
    p Go Fullscreen
</template>

<script>
export default {
  methods: {
    goFullScreen: function () {
      const element = document.documentElement
      const requestMethod = (
        element.requestFullScreen ||
        element.webkitRequestFullScreen ||
        element.mozRequestFullScreen ||
        element.msRequestFullScreen
      )
      if (requestMethod) {
        requestMethod.call(element)
      }
    }
  }
}
</script>

<style scoped>
.eg-fullscreen-button{
  cursor: pointer;
}
</style>
