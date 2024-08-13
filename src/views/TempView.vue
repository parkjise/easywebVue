<script setup>
  const rawHtml = '<a href="#">Link</a>';
  const pid = 10;
  const isButtonDisabled = true;
  const  objectOfAttrs = {
      id: 'container',
      class: 'wrapper'
  }
  const number = 20;
  const ok = false;
  const message = "안녕하세요 !"
  const id = 30;
  const sayHello = (msg) => {
    alert(msg)
  }

  const url = 'http://www.google.com';
  const attributeName = "href";
  const items = [
    {id:0,title:'html'},
    {id:1,title:'css'},
    {id:2,title:'javascript'},
  ]

  const onSubmit = () => {
    alert('제출되었습니다')
  }
</script>
<template>
  <div class="layout">
    <h1>This is an Template page</h1>
    <h1 class="green">{{ msg }}{{ msg2 }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
    <hr>
    <p><span v-html="rawHtml"></span></p>
    <hr>
    <h2>속성 바인딩</h2>
    <div :id="pid"></div>
    <h2>불리언 바인딩</h2>
    <button :disabled="isButtonDisabled">버튼</button>
    <button :disabled="!isButtonDisabled">버튼</button>
    <div :="objectOfAttrs">여러속성 바인드</div>
    <h2>Javascript Expression</h2>
    {{ number + 1 }}
    {{ ok ? '예' : '아니오' }}
    {{ message.split('').reverse().join('') }}
    <div :id="`list-${id}`"></div>
    <!-- <div :title="sayHello('안녕')"></div>
    <p>{{  sayHello('꺼져') }}</p> -->
    <a :href="url">URL</a>
    <a v-bind:[attributeName]="url"> ... </a>
    <a :[attributeName]="url"> ... </a>
    <div v-for="item in items" :key="id">
      {{ item.title }}
    </div>
    <br>
    <br>
    <br>
    <h2>v-on</h2>
    <button type="button" @click="sayHello('꺼져') ">Button</button>
    <button type="button" @mouseover="sayHello('꺼져') ">Button</button>
    <div>
      <button @click="sayHello('제출')">제출</button>
    </div>
    <div>
      <form action="" @submit.prevent="onSubmit">
        <button>제출</button>
      </form>
    </div>
  </div>
</template>

<style>
  @media (min-width: 1024px) {
    .layout {
      min-height: 100vh;
      display: flex;
      align-items: flex-start;
      justify-content: center;
      flex-direction: column;
    }
  }
</style>
