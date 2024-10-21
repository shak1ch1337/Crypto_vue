<template>
    <!--<ul>
        <li v-for="(el, index) in info" :key="index">{{ el.name }}</li>
    </ul>-->
    <select>
        <option v-for="(el, i) in info" @click="getValute(el.id)" :key="i">{{el.name}}</option>
    </select>
</template>

<script>
export default {
    props:{
        info: {
            type: Object,
            required: true
        },
        getValute: {
            type: Function,
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

select {
    padding: 10px 20px;
    font-size: 22px;
    font-family: "Open Sans", sans-serif;
    border-radius: 20px;
    background-color: aquamarine;
}
</style>