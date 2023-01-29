<template>
    <section id="modal-layer" class="modal">
        
        <div class="wrapper">
            <div>Twoje zamowienie</div>
            <ol>
                <li v-for="item in items">
                    
                        <div>{{item.nazwa}}</div>
                        <div>
<!--                            <span v-show="item.bezglutenowe">bezg</span>
                            <span v-show="item.weganskie">vege</span>
                            <span v-show="item.wegetarianskie">weg</span>-->
                        </div>
                    
                </li>
            </ol>
            <slot>Pusto</slot>
        </div>
        
    </section>
</template>
<script>
export default {
    methods: {
        closeModal() {
            return this.$emit('eCloseModal', false)
        }
    },
    props: {
        items: {
            type: Array,
            deafult: () => []
        }
  }
}
</script>
<style scoped lang="scss">
.modal {
   display: flex;
   position: absolute;
   justify-content: center; 
   align-items: center;
   background-color: rgba(0, 0, 0, 0.7);

   .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: white;
    padding: 15px;
    border-radius: 15px;

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
   }
}
</style>