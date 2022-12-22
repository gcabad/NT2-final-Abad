<template>

  <section class="src-components-conversor-temp">
    <h1>Conversor de Temperatura</h1>
    <hr>
    <p>Ingrese Temperatura °C <input type="text" v-model="celsius" ></p>
    <br>
    <div :style="getColor(this.celsius)"> Conv Temperatura °F {{ calcularTemp.fahrenheit }} </div>
    <div :style="getColor(this.celsius)">Conv Temperatura °K {{ calcularTemp.kelvin }} </div>

    <p>Respuestas: 1:c 2:b 3:c 4:a 5:b </p>

  </section>

</template>

<script>

  export default  {
    name: 'src-components-conversor-temp',
    props: [],
    mounted () {

    },
    data () {
      return {
        celsius: '',
      }
    },
    methods: {
      inputValido(input) {
        if(input.length == 0 || isNaN(input)) return false
        else return true
      },
      getColor(input) {
        let resultado = 'black'
        if(this.inputValido(input)){
          let temp = Number(this.celsius)
          if(temp<=0){
            resultado='blue'
          }else if (temp > 0 && temp < 15){
            resultado= 'magenta'
          }else{
            resultado='red'
          }
        } 
        return {color: resultado}

      }
    },
    computed: {
      calcularTemp() {
        let temp = null
        if(!this.inputValido(this.celsius)) return { farenheit: '', kelvin: ''}
        else temp = Number(this.celsius)
        return {
          fahrenheit: (temp * (9/5) + 32),
          kelvin: (temp + 273.15)
        }
      },
    }
}


</script>

<style scoped lang="css">

</style>
