<template>
  <div class="mainBox">
    <HeaderPart/>
  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav> -->
  <router-view/>
  <FooterPart/>
</div>
</template>
<script type="text/javascript">
import HeaderPart from './components/HeaderPart.vue'
import FooterPart from './components/FooterPart.vue'

  export default {
    name: 'App',
    components: {
      HeaderPart,
      FooterPart
    }
  }
</script>
<style lang="scss">

  .mainBox {
    // height: 100vh;
    position: relative;
  }
</style>
