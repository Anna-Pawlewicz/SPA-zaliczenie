<template>
    <div class="label">
      
        <slot>+</slot>
    </div>
</template>
  
  <script>
  export default {
    name: "AddComponent",
    data() {
      return {
      }
    },
    computed: {
    },
    methods: {
    }
  }
  </script>
  
  <style scoped lang="scss">
  .label {
    font-size: 1rem;

    &:hover {
            background-color: rgb(192, 192, 192);
        }
  }

  

  </style>