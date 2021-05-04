<template>
  <transition name="fade">
    <Modal 
    :rooms="rooms" 
    :pressed="pressed" 
    :isModalOpen="isModalOpen"
    @closeModal="isModalOpen = false"
  />
  </transition>
  
  <div class="menu">
    <a v-for="(nav, index) in navs" :key="index">{{ nav }}</a>
  </div>

  <Discount v-if="showDiscount === true"/>


  <button @click="priceSort">가격순정렬</button>
  <button @click="priceSort2">가격역순정렬</button>
  <button @click="ganada">가나다순정렬</button>
  <button @click="sortRevert">되돌리기</button>

  <Card @openModal="isModalOpen = true; pressed = $event"  
  :rooms="room" v-for="(room, index) in rooms" 
  :key="index"/>
</template>


<script>
import oneroom from './oneroom';
import Discount from './components/Discount';
import Modal from './components/Modal'
import Card from './components/Card'


export default {
  name: 'App',
  data() {
    return {
      showDiscount: true,
      roomsOriginal: [...oneroom],
      pressed: 0,
      rooms: oneroom,
      isModalOpen : false,
      navs: ['Home', 'Products', 'About'],
      products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
      reported: [0, 0, 0]
    }
  },
  methods: {
    priceSort() {
      this.rooms.sort((a, b) => {
        return a.price - b.price;
      })
    },
    priceSort2() {
      this.rooms.sort((a, b) => {
        return b.price - a.price;
      })
    },
    ganada() {
      this.rooms.sort((a, b) => {
        return (a.title).localeCompare(b.title);
      })
    },
    sortRevert() {
      return this.rooms = [...this.roomsOriginal];
    },
  },
  
  components: {
    Discount,
    Modal,
    Card,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
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
.room-img {
  width: 100%;
  margin-top: 40px;
}
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.2);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

button {
  display: block;
  text-align: center;
  margin: 0 auto;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

.start {
  opacity: 0;
  transition: all 1s;
}

.end {
  opacity: 1;
}
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s ease;
}
.fade-enter-to {
  opacity: 1;
}
</style>
