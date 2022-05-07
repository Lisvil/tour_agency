<template>
  <div class="home">
    <div class="img">
       <img src="../assets/grece1.jpg" alt="">
       <div class="darken"></div>
       <div class="text_img">
         <p>Подорожувати легко, подорожуй з Travel agency</p>
       </div>
    </div>
    <main>

      <div class="hot_tur" v-for="item in hotTours" :key="item">
        <div class="description">
          <h2>{{ item.name}}</h2>
          <p>
            {{ item.program}}
          </p>
          <router-link :to="{name: 'Tour', params: {id: item.id}}" > <button>Детальніше</button></router-link>
          <!-- <router-link :to="{name: 'Tour', params: {id: item.id}}" > <button @click='sendId(tourInfo[0].id)'>Детальніше</button></router-link> -->
        </div>
        <div class="tour_new tour">
          <img :src="require(`../assets/tours/${item.id}.jpg`)" alt="">
          <div class="name">
            <p>{{ item.name }}</p>
            <p>{{ item.details}}</p>
          </div>
          <div class="short_inf">
            <div>
              {{ item.dateStart }} - {{ item.dateEnd }}
               {{ item.duration }}/{{ item.days}} днів, Авіапереліт з {{ item.departure}}, Все включено
            </div>
            <div class="price">
              <span>{{ item.price }} грн</span>
              <span> за одного</span>
            </div>
          </div>
          <div class="category">
            HOT!
          </div>
        </div>
      </div>
      <ToursPart/>
      <TourOperators/>
    </main>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import ToursPart from '../components/ToursPart.vue'
import TourOperators from '../components/TourOperators.vue'
import {tours} from '../data/data.js'
export default {
  name: 'HomeView',
  components: {
    ToursPart,
    TourOperators,
  },
  data() {
    return{
      hotTours: [],
      // tourInfo: '',
      // tourIdName: "/tour/"
    }
  },
  mounted() {
    tours.forEach((item) => {
      if(item.id.includes('hot')) {
        this.hotTours.push(item);
      }
    });

  },
  methods: {
    // sendId(id) {
    //    this.tourIdName = this.tourIdName + id;
    // }
  }
}
</script>

<style media="screen">

</style>
