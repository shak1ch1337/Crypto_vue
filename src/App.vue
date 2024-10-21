<template>
  <h1>Crypto</h1>
  <Input :changeAmount="changeAmount"/><br>
  
  <div className="sectionBlock">
    <Section :info="info" :index="index" :getValute="getValute"/>
  </div>
  <Button :getCost="getCost" :info="info" :index="index"/><br>
  <!--<p>{{ index }}</p>-->
  <!--<p>{{ coin }}</p>-->
  <!--<p>{{ amount }}</p>-->
  <!--<p>{{ amountRes }}</p>-->
  <!--<p v-for="(el, index) in names" :key="index">{{ el }}</p>-->
  <!--<p v-for="(el, index) in info" :key='index'>{{el.name}}</p>-->
  <span v-if="amountRes != 0">Данное количество этой криптовалюты будет стоить {{ amountRes }} долларов.</span>
  
</template>

<script>
import Input from './components/Input.vue'
import Section from './components/Section.vue'
import Button from './components/Button.vue'
import axios from 'axios'

export default {
  components: { Input, Section, Button },
  data() {
    return {
      index: 0,
      coin: null,
      info: null,
      amount: null,
      amountRes: 0
    }
  },
  methods: {
    // Получение валют для выбора
    getCoins()
    {
      axios.get('https://api.coinlore.net/api/tickers/?start=1&limit=10')
      .then(res => (this.info = res.data.data))
    },
    // Функция, которая передает значение из input'а
    changeAmount(val)
    {
      if (val <= 0)
      {
        this.coin = 0
      }
      else
      {
        this.coin = val
      }
    },
    // Функция для получения информации об определенной валюте
    getCost()
    {
      
      this.amountRes = Number(this.coin) * Number(this.amount)

    },
    // Получение индекса валюты
    getValute(valuta)
    {
      axios.get(`https://api.coinlore.net/api/ticker/?id=${valuta}`).then(result => (this.amount = result.data[0].price_usd))
      //this.index = valuta
    }
  },
  mounted() {
    this.getCoins();
  }
}
</script>

<style scoped>
.sectionBlock {
  display: flex;
  justify-content: space-around;
  margin-top: 50px;
}
span {
  font-size: 40px;
  font-weight: bold;
  display: inline-flex;
  text-align: center;
  color: rgb(221, 174, 6);
  margin-top: 30px
}
</style>