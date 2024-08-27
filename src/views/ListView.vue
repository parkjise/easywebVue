<script >
  export default {
    data(){
      return {
        parentLangs : "web",
        items : [
          {id:1,title:'HTML',desc :'HTML ...'},
          {id:2,title:'CSS',desc :'CSS ...'},
          {id:3,title:'JavaScript',desc :'JavaScript ...'},
        ],
        myObject: {
        title: 'Vue에서 목록을 작성하는 방법',
        author: '홍길동',
        publishedAt: '2016-04-10'
        },
        numbers : [
        1,2,3,4,5
        ],
        sets: [[ 1, 2, 3, 4, 5 ], [6, 7, 8, 9, 10]]
      }
    },
    computed:{
      evenNumbers(){
        return this.numbers.filter(n => n % 2 === 0)
      }
    },
    methods : {
      even(numbers) {
        return numbers.filter(number => number % 2 === 0)
      }
    }
  }
</script>

<template>
  <div class="layout">
    <h1>This is List Rendering page</h1>
    <ul>
      <li v-for="(item,index) in items" :key="item.id">
        {{ parentLangs }} : {{ index }} - {{ item.title }}
      </li>
    </ul>
    <ul>
      <li v-for="value in myObject" :key="value">
        {{  value  }}
      </li>
    </ul>
    <span v-for="n in 10" :key="n">{{ n }}</span>
  </div>
  <hr>
  <ul>
    <template v-for="item in items" :key="item.id">
      <li>
        {{ item.desc }}
      </li>
    </template>
  </ul>
  <h2>필터</h2>
  <ul>
    <li v-for="n in evenNumbers" :key="n">
      {{ n }}
    </li>
  </ul>
  <button @click="this.numbers.push(2)">를릭</button>
  <ul  v-for="numbers in sets" :key="numbers">
    <li v-for="n in even(numbers)" :key="n">
      {{ n }}
    </li>
  </ul>
  <button @click="sets[0].push(4)">를릭</button>
  </template>
<style>

</style>
