<template>
  <div id="app" >
    <app-header></app-header>
    <main class="main">
      <div class="container">
        <app-new-list-item :cars="cars" @carAdded="addCar"> </app-new-list-item>
        <div class="section-list">
          <b :load="calculateTotal()" >Итого: {{totalPrice}}</b>
          <app-list :cars="cars" @carDeleted="deleteCar"></app-list>
        </div>
      </div>
    </main>
    <app-footer></app-footer>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import List from './components/List.vue'
import NewListItem from './components/NewListItem.vue'
import Footer from './components/Footer.vue'
export default {
  name: 'app',
  data () {
    return {
      totalPrice: 0,
      cars: [
        {
          "id": 1,
          "title": "1.6 MT Ambiente 85 л.с. МКПП 1.6 MT Ambiente 85 л.с. МКПП 1.6 MT Ambiente 85 л.с. МКПП",
          "description": "+ доп. опция Радио-навигационная система Amundasen 2DIN, CD, MP3",
          "year": 2012,
          "color": "red",
          "status": "pednding",
          "price": 1689000
        },
        {
          "id":2,
          "title": "1.6 MT Ambiente 85 л.с. МКПП",
          "description": "",
          "year": 2015,
          "color": "white",
          "status": "pednding",
          "price": 2519000
        },
        {
          "id":3,
          "title": "1.8 MT Ambiente 85 л.с. МКПП",
          "description": "",
          "year": 2010,
          "color": "black",
          "status": "out_of_stock",
          "price": 714000
        },
        {
          "id":4,
          "title": "1.8 MT Ambiente 85 л.с. МКПП",
          "description": "",
          "year": 1990,
          "color": "black",
          "status": "out_of_stock",
          "price": 1714000
        },
        {
          "id":5,
          "title": "1.75 MT Ambiente 85 л.с. МКПП",
          "description": "+ доп. опция Радио-навигационная система Amundasen 2DIN, CD, MP3",
          "year": 2018,
          "color": "green",
          "status": "in_stock",
          "price": 954000
        }
      ]
    }
  },
  methods: {
    addCar(car) {
      this.cars.unshift(car);
      this.calculateTotal();
    },
    deleteCar(index) {
      this.cars.splice(index, 1);
      this.calculateTotal();
    },
    calculateTotal() {
      let total = 0;
      this.cars.forEach((element) => total += element.price);
      this.totalPrice = total;
    }
  },
  components: {
    appList: List,
    appNewListItem: NewListItem,
    appHeader: Header,
    appFooter: Footer
  }
}
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/functions";
@import "../node_modules/bootstrap/scss/variables";
@import "../node_modules/bootstrap/scss/mixins";
@import "./assets/scss/base/base";
@import "./assets/scss/base/typography";
@import "./assets/scss/base/utilities";
@import "./assets/scss/layout/grid";
@import "./assets/scss/page/carlist";
@import "./assets/scss/components/button";
@import "./assets/scss/components/shape";
</style>
