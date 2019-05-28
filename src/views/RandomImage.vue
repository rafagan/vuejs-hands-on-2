<template>
    <div>
        <img :src="url" alt="picsum">
    </div>
</template>

<script>
    export default {
        name: 'RandomImage',
        data() {
            return {
                url: `https://picsum.photos/${Math.floor(Math.random() * 800) + 200}`
            }
        }
    }
</script>

<style scoped>

</style>