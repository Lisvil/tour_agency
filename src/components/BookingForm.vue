<template lang="html">
  <div class="booking">
    <div id="darken"></div>
    <div id = "success_booking" v-show="successBooking == true">
      <div>     
        <p>Тур успішно заброньовано</p>
        <button id="ok" @click='hideForm'>OK</button>
      </div>
   </div>
    <div class="form" v-show="successBooking == false">
      <i class="fas fa-times" id="exit" @click='hideForm'></i>
      <form class="booking_form" action="" method="post">
        <h3>Бронювання туру</h3>
        <p>{{ errorText }}</p>
        <div class="details">
          <div class="person_inf">
            <label>Прізвище</label>
            <input type="text" name="surname" id ="surname" v-model='bookedTourClientInfo.surname'>
            <label>Ім'я</label>
            <input type="text" name="name" id = "name" v-model='bookedTourClientInfo.name'>
            <label>По батькові</label>
            <input type="text" name = "patronymic" id = "patronymic" v-model='bookedTourClientInfo.secondName'>
            <label>Дата народження</label>
            <input type = "date" name = "date_of_birth" id="date_of_birth" v-model='bookedTourClientInfo.dateOfBirth'>
            <label>Номер телефону</label>
            <input type="tel" name="phone_number" id="phone_number" v-model='bookedTourClientInfo.phone'>
            <label>Email</label>
            <input type="email" name="email" id="email" v-model='bookedTourClientInfo.email'>
            <label>Адреса</label>
            <input type="text" name="address" id="address" v-model='bookedTourClientInfo.address'>
          </div>
          <div class="booking_inf">
            <label>Тур</label>
            <input type="text" name="tour" id="tour" :value="tourDetails.name" disabled>
            <label>Дати поїздки </label>
            <input type="text" name="date_st" id="date_st" :value="tourDetails.dateStart" disabled>
            <div>-</div>
            <input type="text" name="date_en" id ="date_en" :value="tourDetails.dateEnd" disabled>
            <div class="check">
              <label>Страхування (+{{ insurance }} грн)</label>
              <input type="checkbox" id="insurance" name="insurance" value=0 v-model='checkedInsurance' @change="insuranceAdded">
              <label>Віза <br>(+{{ visa }} грн)</label>
              <input type="checkbox" id="visa" name="visa" value=0 v-model='checkedVisa' @change="visaAdded">
            </div>
            <div class="includes">
              <div><p>Проїзд: </p><span>{{ tourDetails.transfer }}</span></div>
              <div><p>Місто виїзду: </p><span> {{ tourDetails.departure }}</span></div>
              <div><p>Тривалість: </p><span> {{ tourDetails.duration }}</span></div>
              <div><p>Харчування: </p><span> {{ tourDetails.meal }}</span></div>
            </div>
            <div class="price">
              <label>Сума </label>
              <div><input id="sum_hidden" type=hidden><span class="sum_of_tour" id="sum_of_tour"></span><span>{{ tourPrice }} грн</span></div>
            </div>
            <button type='button' id="book_tour" @click='bookTour'>Забронювати</button>
          </div>
        </div>

      </form>
    </div>
  </div>

</template>

<script>
import { clientsInfo } from '../data/clients.js'
export default {
  props: {
    tourDetails: Object
  },
  data() {
    return {
      hideBookingForm: false,
      successBooking: false,
      tourPrice: this.tourDetails.price,
      insurance: 300,
      visa: 500,
      checkedInsurance: false,
      checkedVisa: false,
      errorText: '',
      bookedTourClientInfo: {
        surname: '',
        name: '',
        secondName: '',
        dateOfBirth: '',
        phone: '',
        email: '',
        address: '',
        tourName: this.tourDetails.name,
        tourId: this.tourDetails.id,
        tourDateStart: this.tourDetails.dateStart,
        tourDateEnd: this.tourDetails.dateEnd,
        tourInsurance:'' ,
        tourVisa: '',
        tourTransfer: this.tourDetails.transfer,
        tourDeparture: this.tourDetails.departure,
        tourDuration: this.tourDetails.duration,
        tourMeal: this.tourDetails.meal,
        tourPriceFinal: '',
      }
    }
  },
  mounted() {
    console.log(this.successBooking);
  },
  methods: {
    hideForm() {
      this.$emit('hideForm', this.hideBookingForm);
    },
    insuranceAdded() {
      if(this.checkedInsurance) {
        this.tourPrice += this.insurance;
      } else {
        this.tourPrice -= this.insurance;
      }
      this.bookedTourClientInfo.tourInsurance = this.checkedInsurance;
    },
    visaAdded() {
      if(this.checkedVisa) {
        this.tourPrice += this.visa;
      } else {
        this.tourPrice -= this.visa;
      }
      this.bookedTourClientInfo.tourVisa = this.checkedVisa;
    },
    bookTour() {
      // let isEmpty = false;
      // for(let item of Object.values(this.bookedTourClientInfo)) {
      //   if (item.length == 0 ) {
      //     isEmpty = true;
      //   } else {
      //     isEmpty = false;
      //     break;
      //   }
      // }
      // if(isEmpty) {
      //   let input = document.querySelectorAll(".person_inf input");
      //   input.forEach((item) => {
      //     item.classList.add('error');
      //     this.errorText = 'Заповніть поля форми'
      //     return;
      //   });
      // } else {
      //   this.errorText = '';
      //   let input = document.querySelectorAll(".person_inf input");
      //   input.forEach((item) => {
      //     item.classList.remove('error');
      //   });
      // }

      if (this.bookedTourClientInfo.surname.length < 2) {
        document.querySelector("#surname").classList.add('error');
        this.errorText = 'Прізвище має містити більше ніж 2 символи';
        return;
      } else {
        document.querySelector("#surname").classList.remove('error');
        this.errorText = '';
      }

      if (this.bookedTourClientInfo.name.length < 2) {
        document.querySelector("#name").classList.add('error');
        this.errorText = 'Ім`я має містити більше ніж 2 символи';
        return;
      } else {
        document.querySelector("#name").classList.remove('error');
        this.errorText = '';
      }

      if (this.bookedTourClientInfo.secondName.length < 2) {
        document.querySelector("#patronymic").classList.add('error');
        this.errorText = 'По батькові має містити більше ніж 2 символи';
        return;
      } else {
        document.querySelector("#patronymic").classList.remove('error');
        this.errorText = '';
      }

      if (this.bookedTourClientInfo.phone.length < 12) {
        document.querySelector("#phone_number").classList.add('error');
        this.errorText = 'Не ввірно введений номер';
        return;
      } else {
        document.querySelector("#phone_number").classList.remove('error');
        this.errorText = '';
      }

      if(this.bookedTourClientInfo.email.toLowerCase().match(/^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/))
      {
        this.errorText = '';
        document.querySelector("#email").classList.remove('error');

      }
      else {
        document.querySelector("#email").classList.add('error');
        this.errorText = 'Не ввірно введений email';
        return;
      }


      if (this.bookedTourClientInfo.address.length < 5) {
        document.querySelector("#address").classList.add('error');
        this.errorText = 'Введіть адресу';
        return;
      } else {
        document.querySelector("#address").classList.remove('error');
        this.errorText = '';
      }

      this.bookedTourClientInfo.tourPriceFinal = this.tourPrice;
      clientsInfo.push(this.bookedTourClientInfo);
      this.successBooking = true;


    }
  }
}
</script>

<style lang="scss" scoped>
  .booking {
    display: flex;
  }
  .error {
    border: 1px solid red!important;
  }
  #success_booking {
    display: flex;
  }
</style>
