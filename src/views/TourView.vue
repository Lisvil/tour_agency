<template>
  <div class="">
    <img :src="require(`../assets/${tourId}/${tourId}-main.jpg`)" alt="" id="main_img">
    <div class="tour_charact">
      <h1>{{ currentTour.name }}</h1>
      <h4> {{ currentTour.details }}</h4>
      <div class="inf">
        <div class="text">
          <h3>{{ currentTour.dateStart }} - {{ currentTour.dateEnd }}</h3>
          <p>Проїзд: <span>{{ currentTour.transfer }}</span><i class="fas fa-plane"></i><i class="fas fa-bus"></i></p>
          <p>Місто виїзду: <span>{{ currentTour.departure }}</span></p>
          <p>Тривалість: <span>{{ currentTour.duration }}</span></p>
          <p>Харчування: <span>{{ currentTour.meal }}</span></p>
          <p>Ціна за 1 людину</p>
          <h3>{{ currentTour.price }} грн</h3>
          <button @click="showBookingForm = true">Забронювати</button>
        </div>
        <div class="photo">
          <img  :src="require(`../assets/${tourId}/${tourId}-details.jpg`)">
        </div>
      </div>
      <div class="inf" v-for="(item, index) in currentTour.daysProgram" :key="item">
        <div class="photo_program" v-if="index%2 == 0">
          <img :src="require(`../assets/${tourId}/${tourId}-${index}.jpg`)">
        </div>
        <div class="text_program">
          <h3>День {{ index + 1 }} <div></div></h3>
          <p> {{ item }} </p>
        </div>
        <div class="photo_program" v-if="index%2 != 0">
          <img :src="require(`../assets/${tourId}/${tourId}-${index}.jpg`)">
        </div>
      </div>
    </div>
    <BookingForm v-if="showBookingForm"  @hideForm = 'showBookingForm = value' :tourDetails='currentTour'/>
  </div>
</template>
<script type="text/javascript">
  // import {hotTour} from '../data/data.js'
  import {tours} from '../data/data.js'
  import BookingForm from '../components/BookingForm.vue'


  export default {
    components: {
      BookingForm
    },
    data() {
      return {
        tourId: this.$route.params.id,
        currentTour: '',
        showBookingForm: false
      }
    },

    mounted() {
      // if (this.tourId.includes('hot')){
      //   hotTour.forEach((item) => {
      //     if(item.id == this.tourId) {
      //       this.currentTour = item;
      //     }
      //   });
      // } else {
      //   tours.forEach((item) => {
      //     if(item.id == this.tourId) {
      //       this.currentTour = item;
      //     }
      //   });
      // }
      tours.forEach((item) => {
        if(item.id == this.tourId) {
          this.currentTour = item;
        }
      });
    }
  }
</script>
