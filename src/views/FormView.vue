<script >
  export default {
    data(){
      return {
        message:'',
        message2 : "나트랑 놀러가자",
        multiple : '',
        checked:true,
        checkedNames:[],
        picked:'하나',
        selected01:'',
        selected: '1',
        options: [
          { text: '하나', value: '1' },
          { text: '둘', value: '2' },
          { text: '셋', value: '3' }
        ],
        toggle:false,
        dynamicTrueValue:"네",
        dynamicFalseValue:"아니오",
        pick:'',
        first:'네',
        second:'아니오',
        msg:''
      }
    },
    methods: {
      
    }
  }
</script>

<template>
  <div class="layout">
    <h1>This is Form Input Bindings Page</h1>
    <p>{{ message2 }}</p>
    <input type="text" :value="message" @input="event=>message=event.target.value">
    <p>메시지 : {{ message }}</p>
    <input v-model="message">
    <p>메시지 : {{ message }}</p>
    <h2>여러 줄 텍스트</h2>
    <p style="white-space: pre-line;">{{ multiple }}</p>
    <textarea v-model="multiple" placeholder="여러 줄을 추가해보세요"></textarea>
    <hr>
    <h2>체크박스</h2>
    <input type="checkbox" id="checkbox" v-model="checked" />
    <label for="checkbox">{{ checked }}</label>
    <hr>
    <div>체크된 이름: {{ checkedNames }}</div>
    <input type="checkbox" id="jack" value="젝" v-model="checkedNames">
    <label for="jack">젝</label>

    <input type="checkbox" id="john" value="존" v-model="checkedNames">
    <label for="john">존</label>

    <input type="checkbox" id="mike" value="마이크" v-model="checkedNames">
    <label for="mike">마이크</label>
    <hr>
    <h2>Radio</h2>
    <div>선택한 것: {{ picked }}</div>
      <input type="radio" id="one" value="하나" v-model="picked" />
      <label for="one">하나</label>

      <input type="radio" id="two" value="둘" v-model="picked" />
      <label for="two">둘</label>
    </div>
    <hr>
    <div>
      <h2>Select</h2>
      <div>선택됨: {{ selected01 }}</div>
      <select v-model="selected01">
        <option disabled value="">다음 중 하나를 선택하세요</option>
        <option>가</option>
        <option>나</option>
        <option>다</option>
      </select>
    </div>
    <hr>
    <div>
      <h2>v-for 동적 렌더링</h2>
      <select v-model="selected">
        <option v-for="option in options" :value="option.value" :key="option">
          {{ option.text }}
        </option>
      </select>
      <div>선택됨: {{ selected }}</div>
    </div>
    <hr>
    <div>
      <h2>값 바인딩 하기</h2>
      <!-- `picked`는 선택 시 문자열 "가"입니다. -->
      <input type="radio" v-model="picked" value="가" />
  
      <!-- `toggle`은 true 또는 false입니다. -->
      <input type="checkbox" v-model="toggle" />
  
      <!-- `selected`는 첫 번째 옵션이 선택될 때 문자열 "한글"입니다. -->
      <select v-model="selected">
        <option value="한글">한글</option>
      </select>
      <input
        type="checkbox"
        v-model="toggle"
        :true-value="dynamicTrueValue"
        :false-value="dynamicFalseValue" />
        <h2>라디오</h2>
        <input type="radio" v-model="pick" :value="first" />
        <input type="radio" v-model="pick" :value="second" />
        <p>{{ pick }}</p>
        <hr>
    </div>
      <div>
        <h2>lazy</h2>
        <!-- "input" 대신 "change" 이벤트 후에 동기화됨 -->
        <input v-model.lazy="msg" />
        <p>{{ msg }}</p>
      </div>
</template>
<style>
  .box{
    display: block;
    border: 1px solid #000;
    padding: 20px;
  }
</style>
