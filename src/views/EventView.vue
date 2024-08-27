<script >
  export default {
    data(){
      return {
        count:0,
        name : 'Park Ji se'
      }
    },
    methods: {
      greet(event) {
        // `this`는 메서드가 활성화된 현재 인스턴스를 가리킵니다.
        alert(`안녕 ${this.name}!`)
        // 'event'는 네이티브 DOM 이벤트 객체입니다.
        if (event) {
          alert(event.target.tagName)
        }
      },
      say(message) {
        alert(message)
      },
      warn(message, event) {
        // 이제 네이티브 이벤트 객체에 접근할 수 있습니다.
        if (event) {
          event.preventDefault()
        }
        alert(message)
      },
      doThis(){
        // Stop
        alert('링크 전파를 차단했습니다.')
      },
      onSubmit(){
        // onSubmit
        alert('폼 제출을 막았다')
      },
      doTaht(){
        // .stop.prevent
        alert('기본속성 차단하고 , 링크전파 차단')
      },
      boxClick(){
        alert('boxClick')
      },
      spanClick(){
        // .stop.prevent
        alert('spanClick')
      },
      submit(){
        alert('enter 키가 입력되었습니다')
      },
      onPageDown(){
        alert('페이지다운키가 입력되었습니다')
      }
    }
  }
</script>

<template>
  <div class="layout">
    <div>
      <h1>인라인 핸들러</h1>
      <button @click="count++">클릭</button>
      <div>{{ count }}</div>
    </div>
  </div>
  <hr>
  <div>
    <h1>메서드 핸들러</h1>
    <button @click="greet">클릭</button>
  </div>
  <hr>
  <div>
    <h1>인라인 핸들러 메서드 호출하기</h1>
    <button @click="say('꼬져')">클릭</button>
    <button @click="say('안녕')">클릭</button>
  </div>
  <hr>
  <div>
    <h1>인라인 핸들러에서 이벤트 객체 접근하기</h1>
    <!-- 특수한 키워드인 $event 사용 -->
    <button @click="warn('아직 양식을 제출할 수 없습니다.', $event)">
      제출하기
    </button>
    <!-- 인라인 화살표 함수 사용 -->
    <button @click="(event) => warn('아직 양식을 제출할 수 없습니다.', event)">
      제출하기
    </button>
  </div>
  <hr>
  <div>
    <h1>이벤트 수식어</h1>
    <!-- 클릭 이벤트 전파가 중지됩니다. -->
    <a @click.stop="doThis" href="http://www.naver.com" target="_blank">doThis</a>

    <!-- submit 이벤트가 더 이상 페이지 리로드하지 않습니다. -->
    <form @submit.prevent="onSubmit" action="http://www.naver.com">
      <button>버튼</button>
    </form>

    <!-- 수식어를 연결할 수 있습니다. -->
    <a @click.stop.prevent="doThat" href="http://www.naver.com" target="_blank">stop.prevent</a>

    <!-- 이벤트에 핸들러 없이 수식어만 사용할 수 있습니다. -->
    <form @submit.prevent action="http://www.naver.com">
      <button>버튼</button>
    </form>

    <!-- event.target이 엘리먼트 자신일 경우에만 핸들러가 실행됩니다. -->
    <!-- 예를 들어 자식 엘리먼트에서 클릭 액션이 있으면 핸들러가 실행되지 않습니다. -->
    <div @click="boxClick" class="box">
      <span @click="spanClick" class="box">클릭</span>
    </div>
    <div @click.self="boxClick" class="box">
      <span @click.self="spanClick" class="box"></span>
    </div>
  </div>
  <hr>
  <h2>입력키 수식어</h2>
  <!-- `key`가 `Enter`일 때만 `submit`을 호출합니다 -->
  <input @keyup.enter="submit" />
  <input @keyup.page-down="onPageDown" />
</template>
<style>
  .box{
    display: block;
    border: 1px solid #000;
    padding: 20px;
  }
</style>
