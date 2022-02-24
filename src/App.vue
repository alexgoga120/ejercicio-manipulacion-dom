<template>
  <h1 class="title is-1 has-text-centered">Task manager</h1>
  <HelloWorld/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style lang="sass">

@import "scss/main.scss"

</style>
