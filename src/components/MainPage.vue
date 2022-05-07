<template>
  <div>
    <div class="img">
       <img src="../assets/grece1.jpg" alt="">
       <div class="darken"></div>
       <div class="text_img">
         <p>Подорожувати легко, подорожуй з Travel agency</p>
       </div>
    </div>
    <main>

      <div class="hot_tur">
        <div class="description">
          <h1>Name of tour</h1>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Omnis cum voluptatum laudantium adipisci, ad iure blanditiis ducimus necessitatibus molestias quia, error cumque praesentium possimus officia et. Molestiae eum voluptates, magni.
          </p>
          <!-- <button><a href ="tour_5.php">Детальніше</a></button> -->
          <button><router-link to="/hot-tour">Детальніше</router-link></button>
        </div>
        <div class="tour_new tour">
          <img src="../assets/main3_img.jpg" >
          <div class="name">
            <p>Name of country</p>
            <p>Details of tour</p>
          </div>
          <div class="short_inf">
            <div>
              31 мар на 7 ночей/8 дней, Авиаперелет из Киева, Все включено
            </div>
            <div class="price">
              <span>9 440 грн</span>
              <span>за одного</span>
            </div>
            <!-- <div class="category">
              HOT!
            </div> -->
          </div>
          <div class="category">
            HOT!
          </div>
        </div>
        </div>
      <div class="tours_part">
      <div class="title">
        Тури
        <div></div>
      </div>
      <!--<div class="tours">-->
        <div class="tours">
          <div>
            <div class="tour_1 tour">
              <a href ="tour_1.php">
                <img src="../assets//main_img.jpg" >
                <div class="name">
                  <p class="name_of_tour">Австрія + Баварія: гори, замки і озера</p>
                  <p>Австрія (Целль-ам-Зеє, Інсбрук, Обергургль), Німеччина (Мюнхен), Чехія (Прага, Чеський Крумлов)</p>
                </div>
                <div class="short_inf">
                  <div>
                    31 травня на 6 ночей/7 днів <br>Виїзд з Києва
                  </div>
                  <div class="price">
                    <span>17 275 грн</span>
                    <span>за одного</span>
                  </div>
                </div>
              </a>
            </div>
            <div class="tour_2 tour">
              <a href ="tour_2.php">
                <img src="../assets//tour_2/tour2_img13.jpg">
                <div class="name">
                  <p class="name_of_tour">Грецькі канікули (Оліипійська рів'єра)</p>
                  <p>Греція, Салоніки, Метеора, Лутраки, Афіни</p>
                </div>
                <div class="short_inf">
                  <div>
                    31 мар на 7 ночей/8 дней, Авиаперелет из Киева, Все включено
                  </div>
                  <div class="price">
                    <span>5 988 грн</span>
                    <span>за одного</span>
                  </div>
                </div>
              </a>
            </div>
          </div>
          <div>
            <div class="tour_3 tour">
              <a href ="tour_3.php">
                <img src="../assets//main2_img.jpg" >
                <div class="name">
                  <p class="name_of_tour">Name of country</p>
                  <p>Details of tour</p>
                </div>
                <div class="short_inf">
                  <div>
                    31 мар на 7 ночей/8 дней, Авиаперелет из Киева, Все включено
                  </div>
                  <div class="price">
                    <span>9 440 грн</span>
                    <span>за одного</span>
                  </div>
                </div>
              </a>
            </div>
            <div class="tour_4 tour">
              <a href ="tour_4.php">
                <img src="../assets//main5_img.jpg" >
                <div class="name">
                  <p class="name_of_tour">Name of country</p>
                  <p>Details of tour</p>
                </div>
                <div class="short_inf">
                  <div>
                    31 мар на 7 ночей/8 дней, Авиаперелет из Киева, Все включено
                  </div>
                  <div class="price">
                    <span>9 440 грн</span>
                    <span> за одного</span>
                  </div>
                </div>
              </a>
            </div>
        </div>
      </div>
    </div>
    <div class="turoperators">
      <h3>Туроператори <div></div></h3>
      <div></div>
      <div class="rows">
        <div class="tour_oper_name">
          <div class="icon">
            <img src="../assets//tour_oper/anex4.png">
            <p>AnexTour</p>
          </div>
        </div>
        <div class="tour_oper_name">
          <div class="icon">
            <img src="../assets//tour_oper/coral4.png">
            <p>Coral Travel</p>
          </div>
        </div>
        <div class="tour_oper_name">
          <div class="icon">
            <img src="../assets//tour_oper/tpg.png">
            <p>Travel Professional Group</p>
          </div>
        </div>
      </div>
      <div class="rows">
        <div class="tour_oper_name">
          <div class="icon">
            <img src="../assets//tour_oper/pegas2.jpg">
            <p>Pegas Touristik</p>
          </div>
        </div>
        <div class="tour_oper_name">
          <div class="icon">
            <img src="../assets//tour_oper/join.png">
            <p>Join Up</p>
          </div>
        </div>
        <div class="tour_oper_name">
          <div class="icon">
            <img src="../assets/tour_oper/tui.png">

            <p>TUI Україна</p>
          </div>
        </div>
      </div>
    </div>
    </main>
  </div>
</template>
<!-- <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script> -->
<script>
export default {
  name: 'MainPage',
  props: {
    msg: String
  }
}

</script>
