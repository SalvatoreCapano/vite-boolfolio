<script>

// Components
import AppHeader from './components/AppHeader.vue'

export default {
  name: "App",
  components: {
    AppHeader
  }
};
</script>


<template>
  <AppHeader/>
  <div class="container">
    <router-view></router-view>
  </div>
</template>


<style lang="scss">
@use './style/main.scss' as *;

</style>