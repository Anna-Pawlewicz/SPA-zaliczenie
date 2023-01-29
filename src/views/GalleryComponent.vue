<template>
  <section>
    <h1>Menu</h1>
    <hr first>
    <div>
      <input id="bezgl" type="checkbox" v-model="bezgl" value="bg" /> <label for="bezgl">Bezglutenowe</label>
      <input id="wege" type="checkbox" v-model="wege" value="wg" /> <label for="wege">Wege</label>
      <input id="vegan" type="checkbox" v-model="vegan" value="ve" /> <label for="vegan">Vegan</label>
    </div>
    <div style="text-align: end;">
      <span v-if="!loader" >&euro; 1.00 = {{ kwotaPLN(eurPrice) }}</span>
    </div>
    <p v-if="loader">Pobieram dane...</p>

    <ul>
      <li v-for="item in getData()" :key="item.id">
        <h2>{{ item.nazwa }}</h2>
        <h3>{{ kwotaPLN(item.cena) }}</h3>        
        <img :src="getImgPath(item.obrazek)" :alt="item.nazwa" :title="item.nazwa">
        <button @click="addToCart(item.id)">
          Dodaj do koszyka
        </button>
        <hr>
      </li>
    </ul>
  </section>
</template>

<script>
import axios from "axios";
import jsonData from "./../static/menu_restauracji.json"

export default {
  name: "GalleryComponent",
  emits: ["addCart"],
  data() {
    return {
      eurPrice:0,
      loader: false,
      dishArray: [],
      bezgl: false,
      wege: false,
      vegan: false
    }
  },

  methods: {
      getCurrencyData() {
          return axios.get('https://api.nbp.pl/api/exchangerates/rates/A/EUR/?format=JSON')
              .then((response) => { this.eurPrice = response.data.rates[0].mid;  this.loader = false; })
              .catch((error) => {
                  throw error.response.data;
              });
      },
      getImgPath(name) {
            return `foto/${name}`
      },
      addToCart(dish) {
console.log(`## adding: ${dish}`)
        this.$emit("addCart", dish)
      },
      kwotaPLN(kwota) {
        return new Intl.NumberFormat('pl-PL', { style: 'currency', currency: 'PLN' }).format(kwota)
      },
      getData() {
        return this.dishArray.filter(
          (item) => { 
              let result = true;
              if(this.bezgl) {
                result &= item.bezglutenowe===true
              }
              if(this.wege) {
                result &= item.wegetarianskie===true
              }
              if(this.vegan) {
                result &= item.weganskie===true
              }
              return result
            }
        )
      }
  },
  async mounted() {
    this.loader = true
    this.dishArray = jsonData
    await this.getCurrencyData()
    
  },
  watch: {
    wege(newVal, oldVal) {
      console.log(`wege: ${newVal}`)
    },
    vegan(newVal, oldVal) {
      console.log(`vegan: ${newVal}`)
    }
  }
}
</script>

<style scoped>
hr {
  border-top: 1px solid red;
}

hr[first] {
  border-top: 1px solid green;
}
</style>