<template>
  <div class="shadow-lg md:w-8/12 w-11/12 bg-white m-auto p-4 rounded">
    <TagInput />
  </div>
</template>

<script>
  import TagInput from './components/TagInput.vue';

  export default {
    components: {
      TagInput,
    }
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
