<template>
  <div class="black-bg" v-if="isModalOpen">
    <div class="white-bg">
        <img :src="rooms[pressed].image">
      <h4>{{ rooms[pressed].title }}</h4>
      <div>{{ rooms[pressed].content }}</div>
      <div>{{ rooms[pressed].price }}원</div>
      <button @click="send">close</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'Modal',
    props: {
        rooms: Object,
        pressed: Number,
        isModalOpen: Boolean,
    },
    methods: {
        send() {
            this.$emit('closeModal')
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