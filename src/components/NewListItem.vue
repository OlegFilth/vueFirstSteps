<template>
  <div class="section-form">
    <h1 class="title-primary u-text-center">¡Ay caramba!</h1>
    <form  action="#" class="section-form__form form js-add-car">
      <div class="form__inner">
        <div class="field form__item">
          <input id="name" type="text" v-model.lazy="newCar.title" class="field__input" required>
          <label for="name" class="field__placeholder" :class="{'field__placeholder--filled': newCar.title}" >Название</label>
        </div>
        <div class="field form__item">
          <input id="year" type="text" v-model.lazy="newCar.year" class="field__input" required>
          <label for="year" class="field__placeholder" :class="{'field__placeholder--filled': newCar.year}">Год</label>
        </div>
        <div class="field form__item">
          <input id="price" type="number" v-model.lazy.number="newCar.price" class="field__input" required>
          <label for="price" class="field__placeholder" :class="{'field__placeholder--filled': newCar.price}">Цена</label>
        </div>
        <div class="field form__item">
          <input id="description" type="text" v-model.lazy="newCar.description" class="field__input" required>
          <label for="description" class="field__placeholder" :class="{'field__placeholder--filled': newCar.description}">Описание</label>
        </div>
        <div class="form__item">
          <label for="radio-white" class="radio">
          <input id="radio-white" class="radio__input" v-model.lazy="newCar.color" type="radio" name="color" value="white" required>
          <span class="radio__checkmark circle circle--white"></span>
          </label>
          <label for="radio-black" class="radio">
          <input id="radio-black" class="radio__input" v-model.lazy="newCar.color" type="radio" name="color" value="black" required>
          <span class="radio__checkmark circle circle--black"></span>
          </label>
          <label for="radio-gray" class="radio" >
          <input id="radio-gray" class="radio__input" v-model.lazy="newCar.color" type="radio" name="color" value="gray" required>
          <span class="radio__checkmark circle circle--gray"></span>
          </label>
          <label for="radio-red" class="radio">
          <input id="radio-red" class="radio__input" v-model.lazy="newCar.color" type="radio" name="color" value="red" required>
          <span class="radio__checkmark circle circle--red"></span>
          </label>
          <label for="radio-green" class="radio">
          <input id="radio-green" class="radio__input" v-model.lazy="newCar.color" type="radio" name="color" value="green" required>
          <span class="radio__checkmark circle circle--green"></span>
          </label>
        </div>
        <div class="field form__item">
          <select id="status" class="select" v-model="newCar.status"  name="status" required>
            <option selected disabled="disabled" hidden value="">Cтатус</option>
            <option class="select__option"  value="in_stock" >В наличии</option>
            <option class="select__option"  value="pednding" >Ожидается</option>
            <option class="select__option"  value="out_of_stock">Нет в наличии</option>
          </select>
        </div>
        <div class="form__item"><button class="btn btn--primary" @click.prevent="addNewCar">Отправить</button></div>
      </div>
      {{newCar}}
    </form>
  </div>
</template>

<script>
export default {
  props: ['cars'],
  data() {
    return {
      newCar: {
        id: this.cars.length,
        title: '',
        year: '',
        status: '',
        price: '',
        description: '',
        color: ''
      }
    }
  },
  methods: {
    addNewCar() {
      this.$emit('carAdded', this.newCar);
      this.newCar = {
        title: '',
        year: '',
        price: '',
        discrition: '',
        color: ''
      }
    }
  }
}
</script>

<style lang="scss">
@import "../../node_modules/bootstrap/scss/functions";
@import "../../node_modules/bootstrap/scss/variables";
@import "../../node_modules/bootstrap/scss/mixins";
@import "../assets/scss/abstracts/variables";
@import "../assets/scss/components/form";
</style>
