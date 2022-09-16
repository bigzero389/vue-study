<template>
<div>

  <div class="black-bg" v-if="popup">
    <div class="white-bg">
      <h4>{{ product }}</h4>
      <p>{{ detail }}</p>
      <button @click="popup=false">close</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
  </div>

  <div class="price-list">
<!-- 
    <div v-for="(product, i) in products" :key="i">
      <h4>{{ products[i] }}</h4>
      <p>{{ prices[i] }} 만원</p>
    </div>
 -->
    <div v-for="(product,i) in products" :key="i">
      <!-- <img v-bind:src="`./assets/room${i}.jpg`" class="room-img"> -->
      <!-- <img src="./assets/room0.jpg" class="room-img"> -->
      <img :src="require(`./assets/room${i}.jpg`)" class="room-img">
      <h4 @click="getDetail(i)">{{ products[i] }}</h4>
      <p>{{ prices[i] }} 만원</p>
      <button @click="addReport(i)">허위매물신고</button> <span>신고수: {{ reports[i] }}</span>
    </div>
    <!-- <div>
      <img src="./assets/room1.jpg" class="room-img">
      <h4>{{ products[1] }}</h4>
      <p>{{ prices[1] }} 만원</p>
      <button @click="addReport(1)">허위매물신고</button> <span>신고수: {{ reports[1] }}</span>
    </div>
    <div>
      <img src="./assets/room2.jpg" class="room-img">
      <h4>{{ products[2] }}</h4>
      <p>{{ prices[2] }} 만원</p>
      <button @click="addReport(2)">허위매물신고</button> <span>신고수: {{ reports[2] }}</span>
    </div> -->

  </div>

</div>
</template>

<script>
  import onerooms from './assets/onerooms.js';

  export default {
    name: 'App',
    data() {
      return {
        product: '',
        detail: '',
        popup: false,
        reports: [0, 0, 0],
        prices: [50, 60, 80],
        products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
        details: ['역삼동원룸 상세','천호동원룸 상세','마포구원룸 상세'],
        menus: ['Home', 'Shop', 'About'],
        onerooms : onerooms,
      }
    },
    methods : {
      addReport(i) {
        this.reports[i]++;
      },
      getDetail(i) {
        this.product = this.products[i];
        this.detail = this.details[i];
        this.popup = true;
      },
    },
    components: {}
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    /* margin-top: 60px; */
  }

  body {
    margin: 0;
  }

  div {
    box-sizing: border-box;
  }

  .black-bg {
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    position: fixed;
    padding: 20px;
  }

  .white-bg {
    width: 100%;
    background: white;
    border-radius: 8px;
    padding: 20px;
  }

  .room-img {
    width: 100%;
    margin-top: 40px;
  }

  .menu {
    background: darkslateblue;
    padding: 15px;
    border-radius: 5px;
  }

  .menu a {
    color: white;
    padding: 10px;
  }
</style>