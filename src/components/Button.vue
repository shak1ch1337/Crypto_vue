<template>
    <button @click="getCost()" type="button">Узнать стоимость</button>
</template>

<script>
export default {
    props: {
        getCost: {
            type: Function,
            required: true
        },
        info: {
            type: Object,
            required: true
        },
        index: {
            type: Number,
            required: true
        }
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300..800;1,300..800&display=swap');

button {
    margin: 20px 20px;
    font-size: 20px;
    padding: 5px 20px;
    border-radius: 15px;
    font-family: "Open Sans", sans-serif;
    background-color:  #50c0b9;
    border: 0;
    color:#045651;
}

button:hover{
    padding: 10px 25px;
    background-color:  #00312e;
    color:#ffffff;
    border: 2px solid white;
}
</style>