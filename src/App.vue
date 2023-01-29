<script setup>
import {RouterLink, RouterView} from 'vue-router'
import TopBarComponents from "@/components/TopBarComponents.vue";
import CartComponent from '@/components/CartComponent.vue';
import ModalInfoComponent from "@/components/ModalInfoComponent.vue"
import jsonData from "@/static/menu_restauracji.json"

</script>
<template>
  <head>
    <link href="https://fonts.googleapis.com/css?family=Open+Sans:300,300i,400,400i,600,600i,700,700i|Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500;1,600;1,700|Poppins:300,300i,400,400i,500,500i,600,600i,700,700i" rel="stylesheet">
  </head>
  <div>
    <TopBarComponents>
      <CartComponent :cart="cart" @showCart="toogleModal(true)"/>
    </TopBarComponents>
  </div>
  <div>
    <!--zmiana-->
    <RouterView @addCart="(n) => onaddCart(n)"/>
    <!--koniec zmiany-->
    <footer class="footer">
      <div class="container">
        
          <div class="col-12 text-center">
            <div class="copyright pt-5">
              <p><small>&copy; Anna Pawlewicz 2023</small></p>
            </div>
          </div>
        
      </div>
    </footer>
  </div>

  <ModalInfoComponent v-if="showModal" @eCloseModal="toogleModal($event)" :items="getCart">
    
    <br/>
    <button class="btn" @click="makeOrder">Zamow</button>
    <button class="btn" @click="toogleModal(false)">Zamknij</button>
    
  </ModalInfoComponent>
</template>

<script>
export default {
  name: "TopBarComponents",
  data() {
    return {
      cart: [],
      showModal: false,
      menuData: []
    }
  },
  methods: {
    onaddCart(item) {
      this.cart.push(item)
    },
    toogleModal(parm) {
      return this.showModal = parm
    },

    makeOrder() {
      return this.showModal = false;
    },
  },
  computed: {
    getCart() {
      let cartWithPhotos = []
      this.cart.forEach((dish) => {
        let v = this.menuData.find(menuItem => menuItem.id === dish)
        cartWithPhotos.push(v)
      })
      return cartWithPhotos
    }
  },
  mounted() {
    this.menuData = jsonData;
    console.log(`### ${JSON.stringify(this.menuData)}`)
  },
  watch: {
        cart(newCart, oldCart) {
            console.log(`New cart: ${newCart}`)
        }
    }
}
</script>

<style scoped>
.copyright {
    border-top: 1px solid;
}
.btn {
        padding: 10px 25px;
        margin-top: 10px;
        background-color: green;
        color: white;
        border: unset;
        cursor: pointer;

        &:hover {
            background-color: rgb(5, 161, 18);
        }
    }
</style>
