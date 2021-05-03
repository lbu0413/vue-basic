<template>
  <Modal :rooms="rooms" :isModalOpen="isModalOpen" :pressed="pressed"/>
  <div class="menu">
    <a v-for="(nav, index) in navs" :key="index">{{ nav }}</a>
  </div>

  <Discount />
  <Card :rooms="rooms" :reported="reported" :isModalOpen="isModalOpen"/>
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
      pressed: null,
      rooms: oneroom,
      isModalOpen : false,
      navs: ['Home', 'Products', 'About'],
      products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
      reported: [0, 0, 0]
    }
  },
  methods: {
    increase: function() {
      
    }
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
  background: rgba(0,0,0,0.5);
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
</style>
