<template>
<div class="container">
  <h1 class="header">Vue Calculator</h1>
  <div class="calculator">
    <input class="display" type="text" placeholder="0" v-model="currentValue" disabled="disabled"/>
    <div @click="clear" class="btn">AC</div> 
    <div @click="sign" class="btn">+/-</div>
    <div @click="percent" class="btn">%</div>
    <div @click="divide" class="btn operator">÷</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="multiply" class="btn operator">x</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="minus" class="btn operator">-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="plus" class="btn operator">+</div>
    <div @click="append('0')" class="btn zero">0</div>
    <div @click="dot" class="btn">.</div>
    <div @click="equal" class="btn operator">=</div>
  </div>
  </div>
</template>

<script>
  export default {
    name: 'Calculator',
    data() {
      return {
        previousValue: null,
        currentValue: '',
        operator: null,
        operatorClicked: false
      }
    },
    methods: {
      clear() {
        this.currentValue = ''
      },
      sign() {
        this.currentValue = this.currentValue.charAt() === "-" ? this.currentValue.slice(1) : `-${this.currentValue}`
      },
      percent() {
        this.currentValue = `${parseFloat(this.currentValue) / 100}`
      },
      append(number) {
        if (this.operatorClicked) {
          this.currentValue = ''
          this.operatorClicked = false
        }
        this.currentValue = `${this.currentValue}${number}`
      },
      dot() {
        if (this.currentValue.indexOf('.') === -1) {
          this.append('.')
        }
      },
      setPrevious() {
        this.previousValue = this.currentValue
        this.operatorClicked = true

      },
      divide() {
        this.operator = (a, b) => a / b
        this.setPrevious()
      },

      multiply() {
        this.operator = (a, b) => a * b
        this.setPrevious()
      },

      minus() {
        this.operator = (a, b) => a - b
        this.setPrevious()
      },

      plus() {
        this.operator = (a, b) => a + b
        this.setPrevious()
      },
      equal() {
        this.currentValue = `${this.operator(parseFloat(this.previousValue), parseFloat(this.currentValue))}`
        this.previousValue = null
      }
    }
  }
</script>

<style scoped>
 .container {
   display: flex;
   flex-direction: column;
 }

 .header {
   display: flex;
   justify-content: center;
   align-items: center;
   color: #34495E;
 }
 .calculator {
   margin: 50px auto;
   max-width: 400px;
   display: grid;
   grid-template-columns: repeat(4, 1fr);
   grid-auto-rows: minmax(50px, auto);
   font-size: 40px;
   box-shadow:
    0 2.8px 2.2px rgba(0, 0, 0, 0.034),
    0 6.7px 5.3px rgba(0, 0, 0, 0.048),
    0 12.5px 10px rgba(0, 0, 0, 0.06),
    0 22.3px 17.9px rgba(0, 0, 0, 0.072),
    0 41.8px 33.4px rgba(0, 0, 0, 0.086),
    0 100px 80px rgba(0, 0, 0, 0.12);
 }
 .display {
   max-width: 100%;
   grid-column: 1 / 5;
   height: 70px;
   line-height: 70px;
   text-align: center;
   background-color: lightslategray;
   border: solid 2px #4B5763;
   border-radius: 4px;
   padding: 5px;
   color: white;
   font-size: 40px;
 }

 ::placeholder {
   color: white;
 }

 .zero {
   grid-column: 1 / 3;
 }


.btn {
  position: relative;
  display: inline-block;
  padding: 0.25em 0.5em;
  text-decoration: none;
  color: #FFF;
  background: #fd9535;
  border-radius: 4px;
  box-shadow: inset 0 2px 0 rgba(255,255,255,0.2), inset 0 -2px 0 rgba(0, 0, 0, 0.05);
  font-weight: bold;
  border: solid 2px #d27d00;
  cursor: pointer;
}

.btn:active {/*on Click*/
  box-shadow: 0 0 2px rgba(0, 0, 0, 0.30);
}


.operator {
  background-color: orange;
}

@media screen and (max-width: 424px){
  .container {
     width: 400px;
  }

  .header {
    padding: 20px;
  }
  .calculator {
    padding: 20px;
  }
  
}

</style>
