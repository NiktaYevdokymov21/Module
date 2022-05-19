<template>
  <div>
    <section class="hero">
      <div class="hero-body">
        <p class="title">
          Модульна робота Варіант 8
        </p>
        <p class="subtitle">
          Виконав Евдокимов Микита КН-32
        </p>
      </div>
    </section>
    <section class="section">
      <b-field label="Кільскість дарконів">
        <b-input type="number" v-model="warriors.others.dragon"></b-input>
      </b-field>
      <b-field label="Кільскість мародерів">
        <b-input type="number" v-model="warriors.human.marauder"></b-input>
      </b-field>
      <b-field label="Кільскість лучників">
        <b-input type="number" v-model="warriors.human.archer"></b-input>
      </b-field>
      <b-button type="is-success" @click="count">Обчислити</b-button>
    </section>
    <section class="section">
      <div>{{'Швидкість: ' + speed}}</div>
      <div>{{'Вартість утримання золота: ' + proviand.money + ' Стріл: ' + proviand.arrows + ' Корм: ' + proviand.feed + ' Дівчат: ' + proviand.girl}}</div>
    </section>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      speed: 0,
      proviand: {
        money: 0,
        arrows: 0,
        feed: 0,
        girl: 0,
      },
      warriors: {
        human: {
          marauder: 0,
          archer: 0,
        },
        others: {
          dragon: 0,
        },
      },
    }
  },
  methods: {
    count() {
      if (this.warriors.human.marauder !== 0) this.speed =  5
      else if(this.warriors.human.archer !== 0) this.speed = 7
      else if(this.warriors.others.dragon !== 0) this.speed = 60
      else this.speed = 0
      this.countProviand();
    },
    countProviand() {
      this.proviand.money = parseInt(this.warriors.human.marauder * 2 + this.warriors.human.archer);
      this.proviand.arrows = this.warriors.human.archer !== 0 ? this.warriors.human.archer * 10 : 0;
      this.proviand.feed = this.warriors.others.dragon;
      this.proviand.girl = this.warriors.others.dragon;
    },
  }
}
</script>
