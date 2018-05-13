<template>
  <ul class="list">
     <li class="list__item list__item--title">
      <p class="list__name">Название</p>
      <p class="list__year">Год</p>
      <p class="list__color">Цвет</p>
      <p class="list__status">Статус</p>
      <p class="list__price">Цена</p>
    </li>
    <app-list-item v-for="(car, index) in cars">
      <p class="list__name">{{ car.title }}</p>
        <p class="list__year">{{ car.year}}</p>
        <p class="list__color"><span :class="['circle', 'circle--'+ car.color]"></span></p>
        <p class="list__status" v-if="car.status==='out_of_stock'"> Нет в наличии </p>
        <p class="list__status" v-if="car.status==='pednding'"> В ожидании </p>
        <p class="list__status" v-if="car.status==='in_stock'">В наличии </p>
        <p class="list__description">{{ car.description}}</p>
        <p class="list__price price">
          <span class="price--current">{{ car.price}}</span><br>
          <span class="price--increase"></span><br>
          <span style="font-size: 10px; color:#ff4e61">Надбавка 13%</span>
        </p>
        <button @click="deleteCar(index)" class="btn btn--secondary list__delete">Удалить</button>
    </app-list-item>
  </ul>
</template>


<script>
import ListItem from './ListItem.vue'
export default {
  props: ['cars'],
  components: {
    appListItem: ListItem, 
  }, 
  methods: {
    deleteCar(index) {
      this.$emit('carDeleted', index)
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../../node_modules/bootstrap/scss/functions";
@import "../../node_modules/bootstrap/scss/variables";
@import "../../node_modules/bootstrap/scss/mixins";
@import "../assets/scss/components/list";
</style>

