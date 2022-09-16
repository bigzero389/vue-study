<template>
<div>

  <div class="black-bg" v-if="popup">
    <div class="white-bg">
      <h4>{{ product.title }}</h4>
      <p>{{ product.content }}</p>
      <button @click="popup=false">close</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
  </div>

  <div v-for="(product,i) in products" :key="i" class="price-list">
    <!-- <img v-bind:src="`./assets/room${i}.jpg`" class="room-img"> -->
    <!-- <img src="./assets/room0.jpg" class="room-img"> -->
    <!-- <img :src="require(`./assets/room${i}.jpg`)" class="room-img"> -->
    <img :src="product.image" class="room-img">
    <h4 @click="getDetail(product)">{{ product.title }}</h4>
    <p>{{ product.price }} 만원</p>
    <button @click="addReport(i)">허위매물신고</button> <span>신고수: {{ products[i].report }}</span>
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
        popup: false,
        products: onerooms,
        menus: ['Home', 'Shop', 'About'],
      }
    },
    methods : {
      addReport(i) {
        if (this.products[i].report == undefined) {
          console.log(this.products[i].report);
          this.products[i].report = 0;
        }
        this.products[i].report++;
      },
      getDetail(product) {
        this.product = product;
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