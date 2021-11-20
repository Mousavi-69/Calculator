<template>
  <div class="container">
    <header class="header">
      <div class="input">{{ current || "0" }}</div>
    </header>
    <div class="kybord">
      <div class="ky_top">
        <div @click="clear()" class="buttun operator">AC</div>
        <div class="buttun operator">√ ̅</div>
        <div @click="sign()" class="buttun operator">+/-</div>
        <div @click="percent()" class="buttun operator">%</div>
      </div>
      <div class="ky_bottom">
        <div class="ky_left">
          <div @click="append('1')" class="buttun">1</div>
          <div @click="append('2')" class="buttun">2</div>
          <div @click="append('3')" class="buttun">3</div>
          <div @click="append('4')" class="buttun">4</div>
          <div @click="append('5')" class="buttun">5</div>
          <div @click="append('6')" class="buttun">6</div>
          <div @click="append('7')" class="buttun">7</div>
          <div @click="append('8')" class="buttun">8</div>
          <div @click="append('9')" class="buttun">9</div>
          <div @click="append('0')" class="buttun">0</div>
          <div @click="dot()" class="buttun">.</div>
          <div @click="equal()" class="buttun operator equals">=</div>
        </div>
        <div class="ky_right">
          <div @click="divide()" class="buttun operator">÷</div>
          <div @click="times()" class="buttun operator">×</div>
          <div @click="minus()" class="buttun operator">-</div>
          <div @click="add()" class="buttun operator">+</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "@vue/reactivity";

const current = ref('');
const previous = ref('');
const operator = ref();
const operatorClicked = ref(false);
function append(number: string) {
  if (operatorClicked.value) {
    current.value = "";
    operatorClicked.value = false;
  }
  current.value = current.value + number;
}
function dot() {
  if (current.value.indexOf(".") === -1) {
    append(".");
  }
}
function clear() {
  current.value = "";
}
function sign() {
  current.value =
    current.value.charAt(0) === "-"
      ? current.value.slice(1)
      : `-${current.value}`;
}
function percent() {
  current.value = `${parseFloat(current.value) / 100}`;
}
function setPrevious() {
      previous.value = current.value;
      operatorClicked.value = true;
    }
    function divide() {
     operator.value = (a:number, b:number)  => a / b;
     setPrevious();
    }
   function times() {
       operator.value = (a:number, b:number) => a * b;
      setPrevious();
    }
    function minus() {
       operator.value = (a:number, b:number)  => a - b;
      setPrevious();
    }
   function add() {
     operator.value = (a:number, b:number)  => a + b;
     setPrevious();
    }
  function  equal() {
     current.value = `${operator.value(
        parseFloat(current.value), 
        parseFloat(previous.value)
      )}`;
      previous.value = '';
    }
</script>

<style scoped>
.container {
  background: rgb(230, 230, 230);
}
.header {
  display: block;
}
.input {
  width: 100%;
  box-sizing: border-box;
  height: 200px;
  background: rgb(240, 240, 240);
  border: none;
}
.kybord {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px;
  gap: 10px;
  box-sizing: border-box;
}
.ky_top {
  display: flex;
  gap: 10px;
}
.ky_bottom {
  display: flex;
  gap: 10px;
}
.ky_left {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}
.ky_right {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.buttun {
  display: flex;
  width: 60px;
  height: 60px;
  background-color: rgb(113, 234, 243);
  border-radius: 100%;
  justify-content: center;
  align-items: center;
}
.operator {
  background-color: burlywood;
}
.equals {
  background-color: rgb(243, 238, 170);
}
</style>
