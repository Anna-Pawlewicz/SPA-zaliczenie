<script>


export default {
  data() {
    return {
      showModal: false,
      nameStudent: "",
      addressStudent: "",
    }
  },

  methods: {
    zamow() {
      this.$router.push('/menu')
    },
  }
}

</script>

<template>
  <section class="hero is-primary is-large header-image">
    <div class="hero-head">
    </div>
    <div class="hero-body">
      <div class="container has-text-centered">
        <h1 class="title is-2">
          Witamy na stronie Restauracji Dobry Smak
        </h1>
        <h2 class="subtitle is-5">
          Zapraszamy do składania zamówień
        </h2>
      </div>
    </div>
  </section>
  <div class="hero-cta">
    <nav class="level">
      <div class="level-item has-text-centered">
        <p class="title">Zamówienia
          <a class="button is-primary">
            <span v-on:click="zamow()">Zamów teraz !</span>
          </a>
        </p>
      </div>
    </nav>
  </div>

  
</template>
