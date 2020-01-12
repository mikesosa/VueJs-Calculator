<template>
  <div class="calculator">
    <!-- <h1>Calculator</h1>
    <small> by Michael Sosa</small> -->
    <div class="screen"><span>{{ current || 0 }}</span></div>
    <div class="btn operator2" @click="clear"><span>C</span></div>
    <div class="btn operator2" @click="sign"><span>+/-</span></div>
    <div class="btn operator2" @click="percent"><span>%</span></div>
    <div class="btn operator" @click="divide"><span>/</span></div>
    <div class="btn" @click="append('7')"><span>7</span></div>
    <div class="btn" @click="append('8')"><span>8</span></div>
    <div class="btn" @click="append('9')"><span>9</span></div>
    <div class="btn operator" @click="multiply"><span>x</span></div>
    <div class="btn" @click="append('4')"><span>4</span></div>
    <div class="btn" @click="append('5')"><span>5</span></div>
    <div class="btn" @click="append('6')"><span>6</span></div>
    <div class="btn operator" @click="sub"><span>-</span></div>
    <div class="btn" @click="append('1')"><span>1</span></div>
    <div class="btn" @click="append('2')"><span>2</span></div>
    <div class="btn" @click="append('3')"><span>3</span></div>
    <div class="btn operator" @click="add"><span>+</span></div>
    <div class="btn zero" @click="append('0')"><span>0</span></div>
    <div class="btn" @click="dot"><span>.</span></div>
    <div class="btn operator" @click="result"><span>=</span></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: '0',
      operation: null,
      operanClicked: false,
      prev: null
    }
  },
  methods: {
    setPrev() {
      this.prev = this.current;
      this.operanClicked = true;
    },
    clear() {
      this.current = '';
    },
    sign() {
      if (this.current != 0) {
        this.current = this.current * -1;
      }
    },
    append(number) {
      if (this.current == 0) {
        this.current = ''
      }
      if (this.operanClicked) {
        this.current = '';
        this.operanClicked = false;
      }
      this.current = this.current + number;
    },
    percent() {
      this.current = this.current / 100;
    },
    dot() {
      if (this.current.indexOf(".") == -1) {
        this.append(".")
      }
    },
    divide() {
      this.operation = function(a, b) {
        return a / b
      };
      this.setPrev();
    },
    multiply() {
      this.operation = function(a, b) {
        return a * b
      };
      this.setPrev();
    },
    sub() {
      this.operation = function(a, b) {
        return a - b
      };
      this.setPrev();
    },
    add() {
      this.operation = function(a, b) {
        return a + b
      };
      this.setPrev();
    },
    result() {
      if (this.prev) {
        this.current = this.operation(parseFloat(this.prev), parseFloat(this.current));
      }
      this.prev = ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .calculator {
    margin: auto;
    width: 350px;
    height: 400px;
    font-size: 35px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
    border-radius: 10px;
    box-shadow: 10px 10px 24px -5px rgba(0,0,0,0.75);
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
  }
  .screen {
    grid-column: 1 / 5;
    background-color: black;
    color: white;
  }
  .screen span {
    top: 20px;
    float: right;
    right: 10px;
  }
  .btn {
    background-color: #e0dcdc;
    border: 1px solid #9e9999;
  }
  .btn:hover {
    background-color: #c5c2c2;
    cursor: pointer;
  }
  .btn:active {
    background-color: #9e937d;
  }
  span {
    top: 13px;
    position: relative;
  }
  .zero {
    grid-column: 1 / 3;
  }
  .operator {
    background-color: orange;
    color: white;
  }
  .operator2 {
    background-color: #cac4c4;
  }
</style>
