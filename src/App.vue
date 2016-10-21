<template>
  <div id="app">
    <img class="logo" src="./assets/logo.png">
    <hello></hello>
    <button @click="cal('1')" > 1 </button>
    <button @click="cal('2')" > 2 </button>
    <button @click="cal('3')" > 3 </button><br>
    <button @click="cal('4')" > 4 </button>
    <button @click="cal('5')" > 5 </button>
    <button @click="cal('6')" > 6 </button><br>
    <button @click="cal('7')" > 7 </button>
    <button @click="cal('8')" > 8 </button>
    <button @click="cal('9')" > 9 </button><br>
    <button @click="cal('0')" > 0 </button>
    <button @click="cal('+')" > + </button>
    <button @click="cal('-')" > - </button><br>
    <button @click="cal('*')" > * </button>
    <button @click="cal('/')" > / </button>
    <button @click="clear()" > c </button>
    <button @click="cal('=')" > = </button>
    <br><br> {{num1}} {{operator}} {{num2}} = {{result}}
  </div>
</template>

<script>
import Hello from './components/Hello'

export default {
  components: {
    Hello
  },
  data () {
    return {
      num1: '',
      num2: '',
      operator: '',
      message: '',
      change: 0,
      result: 0
    }
  },
  methods: {
    cal (get) {
      if (get === '+') {
        this.change = 1
        this.operator = '+'
      } else if (get === '-') {
        this.change = 2
        this.operator = '-'
      } else if (get === '*') {
        this.change = 3
        this.operator = '*'
      } else if (get === '/') {
        this.change = 4
        this.operator = '/'
      } else if (get !== '+' && this.change === 0) {
        this.num1 = this.num1 + get
      } else if (this.change === 1 && get !== '=') {
        this.num2 = this.num2 + get
      } else if (get !== '-' && this.change === 0) {
        this.num1 = this.num1 + get
      } else if (this.change === 2 && get !== '=') {
        this.num2 = this.num2 + get
      } else if (get !== '*' && this.change === 0) {
        this.num1 = this.num1 + get
      } else if (this.change === 3 && get !== '=') {
        this.num2 = this.num2 + get
      } else if (get !== '/' && this.change === 0) {
        this.num1 = this.num1 + get
      } else if (this.change === 4 && get !== '=') {
        this.num2 = this.num2 + get
      } else if (get === '=') {
        if (this.change === 1) {
          this.result = parseInt(this.num1) + parseInt(this.num2)
        } else if (this.change === 2) {
          this.result = parseInt(this.num1) - parseInt(this.num2)
        } else if (this.change === 3) {
          this.result = parseInt(this.num1) * parseInt(this.num2)
        } else if (this.change === 4) {
          this.result = parseInt(this.num1) / parseInt(this.num2)
        }
      }
    },
    clear () {
      this.num1 = ''
      this.num2 = ''
      this.result = 0
      this.change = 0
      this.operator = ''
    }
  }
}
</script>

<style>
html {
  height: 100%;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

#app {
  color: #2c3e50;
  margin-top: -100px;
  max-width: 600px;
  font-family: Source Sans Pro, Helvetica, sans-serif;
  text-align: center;
}

#app a {
  color: #42b983;
  text-decoration: none;
}

.logo {
  width: 100px;
  height: 100px
}
</style>
