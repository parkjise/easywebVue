<script >
  export default {
    data(){
      return {
        awesome : true,
        type :'C',
        page : true
      }
    }
  }
</script>

<template>
  <div class="about">
    <h1>This is an Conditional page</h1>
    
    <button @click="awesome = !awesome">전환</button>
    <div>{{ awesome }}</div>
    <h2 v-if="awesome">Vue는 정말 멋지죠 !</h2>
    <h2 v-else>아닌가요?</h2>
    <hr>
    <div>
      <div v-if="type === 'A'">
        A
      </div>
      <div v-else-if="type === 'B'">
        B
      </div>
      <div v-else-if="type === 'C'">
        C
      </div>
      <div v-else>
        A/B/C 아님
      </div>
    </div>
  </div>
  <hr>
    <button @click="page=!page" :class="{active:page}">페이지 전환</button>
    <template v-if="page">
      <h1>제목 1</h1>
      <p>단락 1</p>
      <p>단락 2</p>
      <div v-show="true">World !</div>
    </template>
    <template v-else>
      <h1>제목 2</h1>
      <p>단락 1</p>
      <p>단락 2</p>
      <div v-show="false">World !</div>
    </template>
  </template>

<style>
  /* @media (min-width: 1024px) {
    .about {
      min-height: 100vh;
      display: flex;
      align-items: center;
    }
  } */
  button.active {
    background-color: #000;
    color: #fff;
  }
</style>
