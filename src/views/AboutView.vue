<template>
  <div class="about">
    <div class="" v-for="(item) in arr" :key="item">
      {{ item }} <br>
      <p>**********************************</p> <br>
    </div>
  </div>
</template>


<script type="text/javascript">
import { clientsInfo } from '../data/clients.js'
  export default {
    data() {
      return {
        arr: clientsInfo,
      }
    },
    mounted() {

  }
}
</script>
