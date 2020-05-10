<template>
<div class="container">
  <h1 class="header">Vue Calculator</h1>
  <div class="calculator">
    <div class="display">{{currentValue || '0'}}</div>
    <div @click="clear" class="btn">AC</div> 
    <div class="btn">+/-</div>
    <div class="btn">%</div>
    <div class="btn operator">÷</div>
    <div class="btn">7</div>
    <div class="btn">8</div>
    <div class="btn">9</div>
    <div class="btn operator">x</div>
    <div class="btn">4</div>
    <div class="btn">5</div>
    <div class="btn">6</div>
    <div class="btn operator">-</div>
    <div class="btn">1</div>
    <div class="btn">2</div>
    <div class="btn">3</div>
    <div class="btn operator">+</div>
    <div class="btn zero">0</div>
    <div class="btn">.</div>
    <div class="btn operator">=</div>
  </div>
  </div>
</template>

<script>
  export default {
    name: 'Calculator',
    data() {
      return {
        currentValue: ''
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
 }
 .calculator {
   margin: 50px auto;
   width: 400px;
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
   grid-column: 1 / 5;
   height: 70px;
   line-height: 70px;
   background-color: lightslategray;
   color: white;
 }
 .zero {
   grid-column: 1 / 3;
 }

.btn {
  background-color: #eee;
  border: solid 1px lightgrey; 
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
