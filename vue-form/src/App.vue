<template>

  <div class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지내용</p>
      <button @click="btnClosedModalHandler">x</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(item, index) in menu" :key="index"> {{ item }} </a>
  </div>
  
  
  <h1>{{ logo }}</h1>
  <!-- <div v-for="(item, index) in products" :key="index"> -->

    <div v-for="item in data" :key="item.id">
      <img src="./assets/room1.jpg" class="room-img">
      <h4 :style="style" @click="btnModalOpenHandler">{{ item.title }}</h4>
      <p>{{ item.price }} 만원</p>
      <p>{{ item.content }}</p>
    </div>

  <!-- <div>
    <img src="./assets/room1.jpg" class="room-img">
    <h4 :style="style" @click="btnModalOpenHandler">{{ products[0] }}</h4>
    <p>{{ money[0] }} 만원</p>
    <button @click="btnCountClick(0)">허위매물신고</button>
    <span>신고수 : {{ countArr[0] }}</span>
  </div> -->
  <!-- <div>
    <img src="./assets/room2.jpg" class="room-img">
    <h4 @click="btnModalOpenHandler">{{ products[1] }}</h4>
    <p>{{ money[1] }} 만원</p>
    <button @click="btnCountClick(1)">허위매물신고</button>
    <span>신고수 : {{ countArr[1] }}</span>
  </div> -->
  <!-- <div>
    <img src="./assets/room3.jpeg" class="room-img">
    <h4 @click="btnModalOpenHandler">{{ products[2] }}</h4>
    <p>{{ money[2] }} 만원</p>
    <button @click="btnCountClick(2)">허위매물신고</button>
    <span>신고수 : {{ countArr[2] }}</span>
  </div> -->
</template>

<script>

let products = ['역삼동 원룸', '천호동 원룸', '방배동 원룸']
let money = ['1000', '2000', '3000'];

import data from './data.js';
// import {apple, apple2} from './data.js';

export default {
  name: 'App',
  data(){
    return {
      logo : '부동산'
      , menu : ['Home', 'Shop', 'About']
      , products : products
      , money : money
      , countArr : [0, 0, 0]
      , modal : false
      , data : data
    }
  },
  methods : {
    btnCountClick (index) {
      this.countArr[index] += 1 //this == data의 object
    },
    btnModalOpenHandler () {
      this.modal = true
    },
    btnClosedModalHandler () {
      this.modal = false
    }
    
  },
  components: {

  }
}
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


.menu {
  background: darkslateblue;
  padding: 15px;
  border: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100;
  margin-top: 40px;
}
</style>
