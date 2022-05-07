<template lang="html">
  <div class="tours_part">
  <div class="title">
    Тури
    <div></div>
  </div>
    <div class="tours">
        <div class="tour_1 tour" v-for="item in tourData" :key="item" >
          <router-link :to="{name: 'Tour', params: {id: item.id}}">
              <img :src="require(`../assets/tours/${item.id}.jpg`)" alt="">
              <div class="name">
                <p class="name_of_tour">{{ item.name }}</p>
                <p>{{ item.details }}</p>
              </div>
              <div class="short_inf">
                <div>
                  {{ item.dateStart }} - {{ item.dateEnd }} <br>Виїзд з {{ item.departure }}, Все включено
                </div>
                <div class="price">
                  <span>{{ item.price }}</span>
                  <span> за одного</span>
                </div>
              </div>
            </router-link>
        </div>
  </div>
</div>
</template>

<script>
import {tours} from '../data/data.js'

export default {
  data() {
    return {
      tourData: [],
      tourIdNameLink: "/tour/"
    }
  },
  mounted() {
    tours.forEach((item) => {
      if(!item.id.includes('hot')) {
        this.tourData.push(item);

      } 
    });
  },
  methods: {
  }
}
</script>
<style media="screen">
  .tours {
    flex-wrap: wrap;
  }
</style>
