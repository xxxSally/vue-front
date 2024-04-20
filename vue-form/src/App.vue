<template>
  <todoHeader />
  <todoInput />
  <todoList v-bind:propsdata="todoItems"/>
  <todoFooter />


  <!-- <div class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지내용</p>
      <button @click="btnClosedModalHandler">x</button>
    </div>
  </div>

  <h1>{{ logo }}</h1>
  <div v-for="item in data" :key="item.id">
    <img src="./assets/room1.jpg" class="room-img">
    <h4 :style="style" @click="btnModalOpenHandler">{{ item.title }}</h4>
    <p>{{ item.price }} 만원</p>
    <p>{{ item.content }}</p>
  </div> -->

</template>

<script>
  import data from './data.js';
  import Header from './components/Header.vue'
  import Footer from './components/Footer.vue'
  import Input from './components/TodoInput.vue'
  import List from './components/TodoList.vue'
  // const products = ['역삼동 원룸', '천호동 원룸', '방배동 원룸']
  // const money = ['1000', '2000', '3000'];

// import {apple, apple2} from './data.js';
  export default {
    name: 'App',
    props: [
      'propsdata'
    ],
    data(){
      return {
        data : data
        
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
      todoHeader : Header
        , todoFooter : Footer
        , todoList : List
        , todoInput : Input
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
