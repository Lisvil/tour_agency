<template lang="html">
  <div class="turoperators">
    <h3>Туроператори <div></div></h3>
    <div></div>
    <div class="rows">
      <div class="tour_oper_name" v-for="(item) in tourOperators " :key="item">
        <div class="icon">
          <img :src="require(`../assets/tour_oper/${item}.png`)">
          <p>{{ item }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import {tourOperatorsList} from '../data/data.js'
export default {
  data() {
    return {
      tourOperators: tourOperatorsList,
    }
  }
}
</script>

<style lang="scss" scoped>
  .rows {
    flex-wrap: wrap;
    margin-top: 0!important;
  }
  .tour_oper_name {
    margin: 20px 40px;
    width: 400px;
  }
  .turoperators {
    h3 {
      margin-bottom: 0!important;
    }
  }

</style>
