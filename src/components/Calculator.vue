<template>
    <div class="container">
        <h3 class="label">VueCalculator</h3>
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
            <div class="item">4</div>
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
    </div>
</template>

<script>
export default {

}
</script>

<style>
.container {
    margin: 0 auto;
    width: 300px;
    padding:15px 30px 30px 30px;
    background-color: steelblue;
    border-radius: 7px;
    box-shadow: inset -5px -5px 5px 0px rgba(46,74,117,1),
                inset 5px 5px 5px 0px rgb(129, 179, 255);
}

.label {
    margin: 5px 0 30px 0 ;
    padding: 0;
    color: steelblue;
    text-align: end;
    text-shadow: -1px -1px 1px  rgba(46,74,117,1), 1px 1px 1px rgb(129, 179, 255);
}

.calculator {
    width: 100%;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: 80px repeat(5, 50px);
    gap: 7px;
}
.item {
    background-color: rgb(168, 232, 248);
    border-radius: 3px;
    padding: 10px;
    font-size: 1.5rem;
    border-right: 0.5px solid rgb(50, 91, 114);
    border-bottom: 0.5px solid rgb(50, 91, 114);
    box-shadow: inset 2px 2px 2px 0px rgb(255, 255, 255),
                inset -1px -1px 2px 0px rgb(88, 153, 179),
                -2px -2px 2px 0px rgba(46,74,117,1),
                1px 1px 1px 0px rgb(129, 179, 255);
}
.item:hover:not(.display) {
    box-shadow: inset 2px 2px 3px 0px rgba(3, 34, 65, 0.7),
                -2px -2px 2px 0px rgba(46,74,117,1);
    border-left: 0.5px solid rgb(31, 31, 66);
    border-top: 0.5px solid rgb(31, 31, 66);
    border-right: none;
    border-bottom: none;
}
.display {
    grid-column: 1 / -1;
    height: 40px;
    background: rgb(40, 40, 40);
    color: greenyellow;
    text-align: end;
    padding: 20px 20px 5px 0;
    box-shadow: 2px 2px 2px 0px rgb(129, 179, 255),
                -2px -2px 2px 0px rgba(46,74,117,1);
}
.operator {
    background: orange;
    color: #fff;
       box-shadow: inset 2px 2px 2px 0px rgb(255, 208, 119),
                   inset -1px -1px 2px 0px rgb(177, 116, 2),
                   -2px -2px 2px 0px rgba(46,74,117,1);
}
.operator:hover {
    box-shadow: inset 2px 2px 5px 0px rgb(156, 87, 3);
}
.zero {
    grid-column: span 2;
}




</style>