<template>
  <div class="main-body">
    <div class="screen">
      <h3>{{ digit }}</h3>
    </div>
    <div class="buttons">
      <h2 @click="doOperation('+')" class="btn btn-pwr">+</h2>
      <h2 @click="doOperation('-')" class="btn btn-pwr">-</h2>
      <h2 @click="doOperation('*')" class="btn btn-pwr">×</h2>
      <h2 @click="doOperation('/')" class="btn btn-pwr">÷</h2>
      <h2 @click="addDigit('7')" class="btn">7</h2>
      <h2 @click="addDigit('8')" class="btn">8</h2>
      <h2 @click="addDigit('9')" class="btn">9</h2>
      <h3 @click="calculatePercentage()" class="btn btn-pwr">%</h3>
      <h2 @click="addDigit('4')" class="btn">4</h2>
      <h2 @click="addDigit('5')" class="btn">5</h2>
      <h2 @click="addDigit('6')" class="btn">6</h2>
      <h3 @click="backspace()" class="btn btn-pwr">⇍</h3>
      <h2 @click="addDigit('1')" class="btn">1</h2>
      <h2 @click="addDigit('2')" class="btn">2</h2>
      <h2 @click="addDigit('3')" class="btn">3</h2>
      <h2 @click="clear()" class="btn btn-pwr">C</h2>
      <h2 @click="addDigit('0')" class="btn">0</h2>
      <h2 @click="addDot()" class="btn">.</h2>
      <h2 @click="calculate()" class="btn btn-0 btn-pwr">=</h2>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      digit: "",
      num1: 0,
      sign: "",
      percent: 0,
    };
  },
  methods: {
    addDigit(digit) {
      if (digit === "0" && this.digit.length < 18) {
        console.log(this.digit.length);
        if (this.digit.length > 0) {
          this.digit += digit;
        }
      } else if (digit !== "0" && this.digit.length < 18) {
        this.digit += digit;
      }
    },
    clear() {
      this.digit = "";
    },
    backspace() {
      this.digit = this.digit.slice(0, -1);
    },
    addDot() {
      if (this.digit.length > 0 && this.digit.indexOf(".") === -1) {
        this.digit += ".";
      }
      if (this.digit.length === 0) {
        this.digit += "0.";
      }
    },
    doOperation(sign) {
      this.num1 = parseFloat(this.digit);
      this.digit = "";
      this.sign = sign;
    },
    calculate() {
      if (this.sign === "+") {
        this.num1 += parseFloat(this.digit);
        this.digit = this.num1.toString();
      } else if (this.sign === "-") {
        this.num1 -= parseFloat(this.digit);
        this.digit = this.num1.toString();
      } else if (this.sign === "*") {
        this.num1 *= parseFloat(this.digit);
        this.digit = this.num1.toString();
      } else if (this.sign === "/") {
        this.num1 /= parseFloat(this.digit);
        this.digit = this.num1.toString();
      }
    },
    calculatePercentage() {
      this.percent = this.num1 * (parseFloat(this.digit) / 100);
      if (this.sign === "+") {
        this.num1 += this.percent;
        this.digit = this.num1.toString();
      } else if (this.sign === "-") {
        this.num1 -= this.percent;
        this.digit = this.num1.toString();
      } else if (this.sign === "*") {
        this.num1 *= this.percent;
        this.digit = this.num1.toString();
      } else if (this.sign === "/") {
        this.num1 /= this.percent;
        this.digit = this.num1.toString();
      }
    },
  },
};
</script>

<style>
.screen {
  display: flex;
  justify-content: flex-end;
  align-items: flex-end;
  color: white;
  width: 280px;
  height: 65px;
  background: #37474f;
  border-radius: 10px;
  margin-bottom: 15px;
  padding: 0px 10px;
}
.main-body {
  width: 300px;
  height: 380px;
  border-radius: 10px;
  padding: 10px;
  background: #263238;
}
.buttons {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
}
.btn {
  padding: 7px 20px;
  margin: 2px;
  background: #cfd8dc;
  flex: 1 1 0px;
  border-radius: 5px;
  -moz-user-select: none;
  user-select: none;
  -ms-user-select: none;
  -webkit-user-select: none;
}
.btn-0 {
  flex: 3.7;
}
.btn-pwr {
  color: white;
  align-self: stretch;
  background: #d84315;
}
</style>