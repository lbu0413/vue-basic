<template>
  <div class="black-bg" v-if="isModalOpen">
    <div class="white-bg">
      <h4>{{ rooms[pressed].title }}</h4>
      <div>{{ rooms[pressed].content }}</div>
      <div>{{ rooms[pressed].price }}원</div>
      <!-- <button @click="isModalOpen = false">닫기</button> -->
    </div>
  </div>
</template>

<script>
export default {
    name: 'Modal',
    props: {
        rooms: Array,
        pressed: Number,
        isModalOpen: Boolean,
    }
}
</script>

<style>

</style>