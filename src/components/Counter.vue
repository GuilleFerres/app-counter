<template>
  <h2> {{ customTitle }} </h2>
  <p> {{ counter }} <sup>2</sup> = {{ squareCounter }} </p>
  <div>
      <button @click="increase">+1</button>
      <button @click="decrease">-1</button>
  </div>
</template>

<script>
export default {
    // props: ['title', 'start'],
    props: {
        title: String,
        start: {
            type: Number,
            default: 100,
            required: true, // La propiedad start es obligatoria
            validator( value ){
                return value > 100
            }
        }
    },
    name : 'Counter', // Para identificarlo en el vue.devtools
    data() { // Cualquier propiedad va a ser reactiva
        return {
            counter: this.start
        }
    },
    methods: {
        getSquareValue() {
            return this.counter * this.counter
        },
        increase(){
            this.counter++
        },
        decrease(){
            this.counter--
        }
    },
    computed: { // Propiedades computadas (Se guardan en caché). Solo se vuelve a realizar si counter cambia
        squareCounter() {
            return this.counter * this.counter
        },
        customTitle() {
            return this.title || 'Counter'
            
        }
    }
}
</script>

<style>
    button{
        background-color: #64bb87;
        border-radius: 5px;
        border: 1px solid white;
        color: white;
        cursor: pointer;
        margin: 0 5px;
        padding: 5px 15px;
        transition: 0.3s ease-in-out;
    }
    button:hover{
        background-color: #5aa67b;
        transition: 0.3s ease-in-out;
    }
</style>