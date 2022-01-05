<template>
  <div class="app--container">
  <div class="container">
            <h3 class="calc--title">Hecken-Rechner: Ratzfatz zum Ergebnis</h3>

            <p class="calc--text">Unser neuer Heckenrechner Lorem ipsum dolor sit amet consectetur adipisicing elit. Saepe possimus itaque optio consequuntur culpa quisquam autem dolorem aliquam, cum, aliquid, minima omnis reprehenderit dicta at.</p>
          
            <form class="form--input" v-on:submit.prevent="calcResult">
              
              <Slider
              class="slider--input"
              v-model="value" 
              :min="1" 
              :max="100"
              after="test"
              v-bind="value" 
              :format="{
                suffix: 'm',
                decimals: 0 
                }" 
            />
              <button @click="calcResult" class="calc--btn">Jetzt berechnen</button>
            </form>
            <p class="calc--alert"><small>*Bitte geben Sie einen Wert in m* an.</small></p>

            <div  v-if="showResult">
                <h4>Ihr Ergebnis:</h4>
                <p>Für Ihren Gartenabschnitt benötigen Sie: <span class="calc--result" :key="product.id" v-for="product in products"> <span class="calc--result__userinput">{{ result }}</span> x {{product.name}}</span> (das entspricht insgesamt {{ rawPlants }} Heckenpflanzen)</p>
            </div>

        </div>
        <img class="image--box" src="https://einhorn.my/wp-content/uploads/woocommerce-placeholder.png" alt="placeholder">
  </div>
</template>

<script>
  import Slider from '@vueform/slider'
  
  
  export default {
    
    components: {
      Slider,
    },
    data() {
      return {
        value: 5,
        calcData: 0.62, 
        products: [
            { name: "Hainbuche, ca. 62 x 61 x 113 cm",
              id: 1}
            ],
            rawPlants: '',
            result: '',
            showResult: false
      }
    },
    methods: {
      calcResult() {
        if ( this.value == 0 ) {
          this.showResult = false
        } else {
          this.showResult = true
          this.result = Math.ceil( this.value / this.calcData )
          this.rawPlants = this.result * 4
          console.log(this.value)
        } 
      }
    }
  }
</script>

<style src="@vueform/slider/themes/default.css"></style>
<style src="./style.css"></style>