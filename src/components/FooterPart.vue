<template lang="html">
  <div class="footerPart">
    <footer>
      <div class="inform">
      <div class="contacts">
        <p><i class="fas fa-phone"></i>Телефон</p>
        <p><i class="fas fa-phone"></i>Телефон</p>
        <p> <i class="fas fa-envelope"></i>tyrism@gmail.com.ua</p>
        <address>
        <i class="fas fa-home"></i>  м. Київ вул. Хрещатик 53,
        </address>
      </div>
      <div class="socials">
        <div class ="up" @click="scrollTop">
          <i class="fas fa-arrow-up"></i>
        </div>
        <div class="teleg">
          <i class="fab fa-telegram-plane"></i>
        </div>
        <div class="face">
          <i class="fab fa-facebook-f"></i>
        </div>
        <div class="inst">
          <i class="fab fa-instagram"></i>
        </div>
        <div class="youtube">
          <i class="fab fa-youtube"></i>
        </div>
      </div>
    </div>
      <p class="all_rights">
        Всі права захищено &copy;
      </p>
    </footer>
  </div>
</template>

<script>
export default {

  methods: {
    scrollTop() {
      window.scrollTo({
        top: 0,
        left: 0,
        behavior: 'smooth'

      });
    }
  }
}
</script>

<style lang="scss" scoped>
.footerPart {

  }
</style>
