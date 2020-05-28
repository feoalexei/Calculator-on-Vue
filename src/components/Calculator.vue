<template>
  <div class="calculator">
      <div class="item display">3,14348345783467</div>
      <div class="item">AC</div>
      <div class="item">+/-</div>
      <div class="item">%</div>
      <div class="item operator">/</div>
      <div class="item">7</div>
      <div class="item">8</div>
      <div class="item">9</div>
      <div class="item operator">*</div>
      <div class="item">7</div>
      <div class="item">5</div>
      <div class="item">6</div>
      <div class="item operator">-</div>
      <div class="item">1</div>
      <div class="item">2</div>
      <div class="item">3</div>
      <div class="item operator">+</div>
      <div class="item zero">0</div>
      <div class="item">.</div>
      <div class="item operator">=</div>
      
  </div>
</template>

<script>
export default {

}
</script>

<style>
.calculator {
    width: 300px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(6, 50px);
}
.item {
    border: 1px solid #aeaeae;
    padding: 10px;
    font-size: 1.5rem;
}
.display {
    grid-column: 1 / -1;
    background: rgb(40, 40, 40);
    color: greenyellow;
}
.operator {
    background: orange;
    color: #fff;
}
.zero {
    grid-column: span 2;
}


</style>