<template>
    <input @input="changeAmount($event.target.value)" className='in' type="number" placeholder="Введите число">
</template>

<script>
export default {
    props: {
        changeAmount: {
            type: Function,
            required: true
        }
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300..800;1,300..800&display=swap');
.in {
    font-size: 22px;
    width: 500px;
    border: transparent;
    border-radius: 25px;
    padding: 10px;
    outline: none;
    font-family: "Open Sans", sans-serif;
}
</style>