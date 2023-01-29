<template>
    <head>
        <link href="https://cdn.jsdelivr.net/npm/boxicons@latest/css/boxicons.min.css" rel="stylesheet">
    </head>
    <a @click="gotoCart" href="#">
        <span class="bx bx-cart cart" :class="{ notEmpty: isCartNotEmpty()}"></span>
        <span v-show="!isCartEmpty">&nbsp;DAŃ: {{ cartItemsCount }} szt.</span>
    </a>
</template>
  
  <script>
  export default {
    name: "CartComponent",
    emits: ["showCart"],
    props: {
        cart: Array
    },
    data() {
      return {
        isNotEmpty: this.isCartEmpty
      }
    },
    computed: {
        isCartEmpty() {
            return this.cart.length === 0
        },
        cartItemsCount() {
            return this.cart.length
        }
    },
    methods: {
      isCartNotEmpty() {
        return this.cart.length > 0
      },
      gotoCart() {
        this.$emit("showCart")
      }
    }
  }
  </script>
  
  <style scoped lang="scss">
  .cart {
    font-size: 2rem;
    padding: 7px;
    
    &:hover {
            background-color: rgb(192, 192, 192);
        }
  }
  .notEmpty {
    color: blue;
  }

  

  </style>