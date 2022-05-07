<template lang="html">
  <div class="container">
    <div class="nav-bar">
      <div class="nav-bar-item" v-for="item in toursInfo" :key="item" @click="chooseTour(item.id)" v-bind:id="item.id">
        <p class="nav-bar-tour-name">{{ item.name }}</p>
      </div>
    </div>
    <div class="lists_part">
      <div class="lists_part_nav">
        <button class="list_btn active" @click="chooseTypeOfList('generalList')" id="generalList">Списки туристів </button>
        <button class="list_btn" @click="chooseTypeOfList('visalList')" id="visalList">Списки на візу </button>
        <button class="list_btn" @click="chooseTypeOfList('insurancelList')" id="insurancelList">Списки на страхування </button>
      </div>
      <div class="lists_part_tourists_info">
        <table>
          <tr class="tourists_info_header">
            <th>№</th>
            <th>Surname</th>
            <th>Name</th>
            <th>Second Name</th>
            <th>Дата народження</th>
            <th>Email</th>
            <th>Адреса</th>
            <th>Номер телефону</th>
          </tr>
          <tr v-for="(item, index) in getClientsForCurrentTour()" :key="item">
            <td>{{ index+1 }}</td>
            <td>{{ item.surname }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.secondName }}</td>
            <td>{{ item.dateOfBirth }}</td>
            <td>{{ item.email }}</td>
            <td>{{ item.address }}</td>
            <td>{{ item.phone }}</td>


          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import {clientsInfo} from '../data/clients.js'
import {tours} from '../data/data.js'
export default {
  data() {
    return {
      clientsInfo: clientsInfo,
      toursInfo: tours,
      currentId: '',
      typeOfList: 'generalList'
      // clientsForCurrentTour: []
    }
  },
  methods: {
    chooseTour(id) {
      let arr = document.querySelectorAll('.nav-bar-item');
      arr.forEach((item) => {
        item.classList.remove("tour_active");
      });
      document.getElementById(id).classList.add("tour_active")
      this.currentId = id;
    },
    getClientsForCurrentTour() {
      switch (this.typeOfList) {
        case 'generalList':
          return this.clientsInfo.filter(client => {
            if (this.currentId == client.tourId)
              return client
            });
        case 'visalList':
        return this.clientsInfo.filter(client => {
          if ((this.currentId == client.tourId) && client.tourVisa)
            return client
          });
        case 'insurancelList':
        return this.clientsInfo.filter(client => {
          if ((this.currentId == client.tourId) && client.tourInsurance)
            return client
          });

      }
      // return this.clientsInfo.filter(client => {
      //   if (this.currentId == client.tourId)
      //     return client
      //   })
      },
    chooseTypeOfList(listType) {
      this.typeOfList = listType;
      let arr = document.querySelectorAll('.list_btn');
      arr.forEach((item) => {
        item.classList.remove("active");
      });
      document.getElementById(listType).classList.add("active")
    }
    }
  }


// this.clientsForCurrentTour = []
// clientsInfo.forEach(item => {
//   if (id == item.tourId) {
//     this.clientsForCurrentTour.push(item)
//   }
// });

</script>

<style lang="css" scoped>
</style>
