<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a class="navbar-item" href="/">
        <img src="@/assets/Logo.png" style="width:200px;">
      </a>

      <a role="button" class="navbar-burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample" @click="showMenuBurger(!showMobileMenu)">
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>

    <div id="navbarBasicExample" class="navbar-menu" :class="{ 'show-burger': showMobileMenu }">
      <div class="navbar-start">
        <RouterLink to="/" class="navbar-item">Witamy</RouterLink>
        <RouterLink to="/menu" class="navbar-item">Menu</RouterLink>
        <RouterLink to="/contact" class="navbar-item">Kontakt</RouterLink>
      </div>

      <div class="navbar-end">
        <div class="navbar-item">
          <slot></slot>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "TopBarComponents",
  data() {
    return {
      showMobileMenu: false
    }
  },

  methods: {
    showMenuBurger(state) {
      this.showMobileMenu = state
    },
  }
}
</script>

<style scoped>
.navbar-item img {
  max-height: unset;
}

.show-burger {
  display: block;
}

.router-link-active {
  border-color: rgb(192, 192, 192);
  border-width: 0.2em;
  border-style: solid;
}

</style>