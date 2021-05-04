<template>
  <div>
    <img :src="rooms.image" class="room-img">
    <h4 @click="send">{{ rooms.title }}</h4>
    <p>{{ rooms.price }}원</p>
    <p>{{ rooms.content }}</p>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        rooms: Object,
    },
    methods: {
        send() {
            this.$emit('openModal', this.rooms.id)
        },
    }
}
</script>

<style>

</style>