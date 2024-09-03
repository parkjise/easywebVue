<script >
  export default {
    mounted() {
    console.log(`컴포넌트가 마운트 됐습니다.`)
    },
    beforeMount(){
      console.log('마운트 이전')
    },
    beforeUpdate(){
      console.log('업데이트 이전')
    },
    updated(){
      console.log('업데이트 완료')
    },
    data(){
      return {
        count:0
      }
    }
  }
</script>

<template>
  {{  console.log('템플릿 컴파일 시작') }}
  <div class="layout">
    <h1>Lifecycle Hooks</h1>
    <button @click="count++">+</button>
    <div id="counter">{{ count }}</div>
    </div>
    {{  console.log('템플릿 컴파일 완료') }}
</template>
<style>
  .box{
    display: block;
    border: 1px solid #000;
    padding: 20px;
  }
</style>
