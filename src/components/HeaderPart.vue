<template>
  <header>
    <div class="logo">
      <img src="../assets/logo1.png">
      <router-link to="/"><span class="home_link">Travel agency</span></router-link>
    </div>
    <div class="menu">
      <router-link :to="{ name: 'Lists', params: {} }">Списки</router-link>
      <!-- <a href="insurance_list.php">Додати тур</a>
      <a href="visa_list.php">Візи</a>
      <span id="user_name">User name</span>
      <a href="" id="exit_btn">Вийти</a> -->
    </div>
  </header>
</template>

<style lang="scss">
  .home_link {
    color: #fff;
  }
  .logo {
    height: 64px;

    img {
      height: 70px!important;
      width: 80px!important;
    }
  }
</style>
