<template>
<div>

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
    <div>
      <h4>{{ products[0] }}</h4>
      <p>{{ prices[0] }} 만원</p>
      <button @click="increasingReport(0)">허위매물신고</button> <span>신고수: {{ reports[0] }}</span>
    </div>
    <div>
      <h4>{{ products[1] }}</h4>
      <p>{{ prices[1] }} 만원</p>
      <button @click="increasingReport(1)">허위매물신고</button> <span>신고수: {{ reports[1] }}</span>
    </div>
    <div>
      <h4>{{ products[2] }}</h4>
      <p>{{ prices[2] }} 만원</p>
      <button @click="increasingReport(2)">허위매물신고</button> <span>신고수: {{ reports[2] }}</span>
    </div>

  </div>

</div>
</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        reports: [0, 0, 0],
        prices: [50, 60, 80],
        products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
        menus: ['Home', 'Shop', 'About'],
      }
    },
    methods : {
      increasingReport(i) {
        this.reports[i]++;
      }
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