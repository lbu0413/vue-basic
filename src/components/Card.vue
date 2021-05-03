<template>
  <div v-for="(room, index) in rooms" :key="index">
    <img :src="room.image" class="room-img">
    <h4 pressed = "index">{{ room.title }}</h4>
    <p>{{ room.price }}원</p>
    <p>{{ room.content }}</p>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        rooms: Array,
        reported: Array,
        isModalOpen: Boolean,
    }
}
</script>

<style>

</style>