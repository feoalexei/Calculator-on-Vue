<template>
    <div class="container">
        <h3 class="label">VueCalculator</h3>
        <div class="calculator">
            <div class="item display">{{ current || '0'}}</div>
            <div class="item" @click="clear">AC</div>
            <div class="item" @click="switchSign">+/-</div>
            <div class="item" @click="percent">%</div>
            <div class="item operator" 
                @click="divide">/</div>
            <div class="item" @click="input('7')">7</div>
            <div class="item" @click="input('8')">8</div>
            <div class="item" @click="input('9')">9</div>
            <div class="item operator"
                @click="multiplicate">*</div>
            <div class="item" @click="input('4')">4</div>
            <div class="item" @click="input('5')">5</div>
            <div class="item" @click="input('6')">6</div>
            <div class="item operator"
                @click="substract">-</div>
            <div class="item" @click="input('1')">1</div>
            <div class="item" @click="input('2')">2</div>
            <div class="item" @click="input('3')">3</div>
            <div class="item operator"
                @click="add">+</div>
            <div class="item zero" @click="input('0')">0</div>
            <div class="item" @click="dot">.</div>
            <div class="item operator"
                @click="result">=</div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            previous: null,
            current: '',
            operator: null,
            operatorClicked: false,
        }
    },
    // filters: {
    //     maxInput() {
    //         if (this.current.length > 5)
    //         console.log('Error')
    //         return;
    //     }
    // },
    methods: {
        clear() {
            this.current = '';
        },
        switchSign() {
            // this.current = this.current.charAt(0) === '-' 
            //     ? this.current.slice(1)
            //     : `-${this.current}`;
            this.current *= -1;
        },
        percent() {
            this.current = `${parseFloat(this.current) / 100}`;
        },
        input(number) {
            if (this.operatorClicked) {
                this.current = '';
                this.operatorClicked = false;
            }
            
            this.current = `${this.current}${number}`;
            
            
        },
        dot() {
            if (!this.current.includes('.')) {
                this.input('.');
            } 
        },
        setPrevious() {
            this.current = parseFloat(this.current);
            this.previous = this.current;
            this.operatorClicked = true;
        },
        divide() {
            this.operator = (a, b) => a / b;
            this.setPrevious();
        },
        multiplicate() {
            this.operator = (a, b) => a * b;
            this.setPrevious();
        },
        substract() {
            this.operator = (a, b) => a - b;
            this.setPrevious();
        },
        add() {
            this.operator = (a, b) => a + b;
            this.setPrevious();
        },
        result() {
            this.current = `${this.operator(
                parseFloat(this.previous), 
                parseFloat(this.current)
            )}`;
            this.previous = 0;
            this.operatorClicked = true;
        }
    }
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
    font-size: 1.8rem;
    border-right: 0.5px solid rgb(50, 91, 114);
    border-bottom: 0.5px solid rgb(50, 91, 114);
    box-shadow: inset 2px 2px 2px 0px rgb(255, 255, 255),
                inset -1px -1px 2px 0px rgb(88, 153, 179),
                -2px -2px 2px 0px rgba(46,74,117,1),
                1px 1px 1px 0px rgb(129, 179, 255);
    cursor: pointer;
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
    font-family: 'Digital-7';
    font-size: 2.5rem;
    grid-column: 1 / -1;
    height: 40px;
    background: rgb(50, 50, 50);
    color: greenyellow;
    text-align: end;
    padding: 15px 20px 15px 0;
    box-shadow: 2px 2px 2px 0px rgb(129, 179, 255),
                -2px -2px 2px 0px rgba(46,74,117,1);
                overflow: hidden;
}

.operator {
    background: orange;
    color: #fff;
       box-shadow: inset 2px 2px 2px 0px rgb(255, 208, 119),
                   inset -1px -1px 2px 0px rgb(177, 116, 2),
                   -2px -2px 2px 0px rgba(46,74,117,1);
}
.operator:nth-of-type(3n) {
    padding-top: 15px;
}
.operator:nth-of-type(3n + 1) {
    padding-top: 5px;
}
.operator:hover {
    box-shadow: inset 2px 2px 5px 0px rgb(156, 87, 3);
}

.zero {
    grid-column: span 2;
}

</style>