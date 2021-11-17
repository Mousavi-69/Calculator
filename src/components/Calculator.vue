<template>
  <div class="container">
    <header class="header">
      <input class="input" type="text" />
    </header>
    <div class="kybord">
     
      <div class="buttun">1</div>
      <div class="buttun">2</div>
      <div class="buttun">3</div>
      <div class="buttun">4</div>
      <div class="buttun">5</div>
      <div class="buttun">6</div>
      <div class="buttun">7</div>
      <div class="buttun">8</div>
      <div class="buttun">9</div>
      <div class="buttun">0</div>
      <div class="buttun operator ">AC</div>
      <div class="buttun operator">C</div>
      <div class="buttun operator">×</div>
      <div class="buttun operator">+</div>
      <div class="buttun operator">÷</div>
      <div class="buttun operator equals">=</div>
      <div class="buttun operator">+/-</div>
      <div class="buttun operator">%</div>
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
.container {
  background: rgb(209, 209, 209);
}
.header {
  display: block;
}
.input {
  width: 100%;
  box-sizing: border-box;
  height: 150px;

}
.kybord {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  row-gap: 5px;
  justify-items: center;
  padding: 20px;
}
.buttun {
  display: flex;
  width: 50px;
  height: 50px;
  background-color: rgb(113, 234, 243);
  border-radius: 100%;
  justify-content: center;
  align-items: center;

}
.operator{
    background-color: burlywood;
}
.equals{
    background-color: rgb(243, 238, 170);
}
</style>
