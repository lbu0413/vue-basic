<template>
    <div class="discount">
        <h4>지금 결제하면 {{ percentage }}% 할인</h4>
    </div>
</template>

<script>
export default {
    name: 'Discount',
    data() {
        return {
            percentage: 3,
        }
    },
    mounted() {
        var ticking = setInterval(() => {
            this.percentage--;
            if(this.percentage == 0) {
            clearInterval(ticking)
        }
        }, 1000) 
    },
}
</script>

<style>

</style>