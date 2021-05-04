<template>
  <div class="black-bg" v-if="isModalOpen">
    <div class="white-bg">
        <img :src="rooms[pressed].image">
      <h4>{{ rooms[pressed].title }}</h4>
      <div>{{ rooms[pressed].content }}</div>
      <input v-model="month">
      <div> {{ month }}개월 선택: {{ month * rooms[pressed].price }}원</div>
      <button @click="send">close</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'Modal',
    data() {
        return {
            month: 1,
        }
    },
    watch: {
        month(a) {
            if(a > 12) {
                alert('no such monhts')
            }
            if(isNaN(a)) {
                alert('Only numbers allowed')
                this.month = 1;
            }
        }
    },
    props: {
        rooms: Object,
        pressed: Number,
        isModalOpen: Boolean,
    },
    methods: {
        send() {
            this.$emit('closeModal')
        }
    },
    beforeUpdate() {
        if(this.month == 2) {
            alert('we do not have options for 2 months')
            this.month = 3;
        }
    }
}
</script>

<style scoped>
    img {
        width: 40%;
    }
    button {
        margin-top: 10px;
        outline: none;
        border: none;
        padding: 10px;
        cursor: pointer;
    }
</style>