<template>
<div id="calc">
  <div class="screen">{{ screen }}</div>
  <div @click="clear()" class="btn clear">C</div>
  <div @click="evaluate()" class="btn equal">=</div>

  <div @click="concatNum('1')" class="btn num">1</div>
  <div @click="concatNum('2')" class="btn num">2</div>
  <div @click="concatOp('*')" class="btn">*</div>

  <div @click="concatNum('3')" class="btn num">3</div>
  <div @click="concatNum('4')" class="btn num">4</div>
  <div @click="concatOp('+')" class="btn">+</div>

  <div @click="concatNum('5')" class="btn num">5</div>
  <div @click="concatNum('6')" class="btn num">6</div>
  <div @click="concatOp('-')" class="btn">-</div>

  <div @click="concatNum('7')" class="btn num">7</div>
  <div @click="concatNum('8')" class="btn num">8</div>
  <div @click="concatOp('/')" class="btn">/</div>

  <div @click="concatNum('9')" class="btn num">9</div>
  <div @click="concatNum('0')" class="btn num">0</div>
</div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'App',
  setup(){
    let screen = ref(0);

    let concatNum = (num) => {
       screen.value === 0 ? (screen.value = num) : (screen.value += 1);
    }
    let concatOp = (op) => {
        if(screen.value === "" || screen.value === 0){
            if(op == '-'){
              screen.value = op;
              return;
            } else{
              return;
            }
        }
          screen.value += op;
    }
     
     let clear = () => {
        screen.value = 0;
     } 

     let evaluate = () => {
        screen.value = eval(screen.value);
     }

    return{ screen, concatNum, concatOp, clear, evaluate }
  }
}
</script>

<style>
#calc{
    border: 2px solid black;
    max-width: 400px;
    margin: 0 auto;
    border-radius: 5px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}
.screen{
    width: 100%;
    background: black;
    color: greenyellow;
    text-align: right;
    font-size: 30px;
    padding: 15px;
}
.btn{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding-top: 5px;
  padding-bottom: 5px;
  margin: 5px;
  color: white;
  background-color: rgb(5, 121, 139);
  font-weight: bold;
  width: 26%;
  border-radius: 50%;
  cursor: pointer;
  text-align: center;
}
.btn:hover{
  opacity: 0.5;
}
.btn.clear{
    background-color: darkred;
    width: 40%;
    border-radius: 0;
}
.btn.equal{
    background-color: darkblue;
    width: 40%;
    border-radius: 0;
}
</style>
