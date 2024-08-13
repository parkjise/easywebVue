<script>
export default {
  data() {
    return {
      author: {
        name: 'John Doe',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ]
      },
      firstName: 'Brad',
      lastName : 'me'
    }
  },
  computed: {
    // 계산된 값을 반환하는 속성
    publishedBooksMessage() {
      // `this`는 컴포넌트 인스턴스를 가리킵니다.
      return this.author.books.length > 0 ? 'Yes' : 'No'
    },
    fullName: {
      get(){
        return this.firstName + ' ' + this.lastName
      },
      set(newValue){
        [this.firstName,this.lastName] = newValue.split(' ');
      }
    }
  }
}
</script>

<template>
  <div>
    <p>책을 가지고 있다:</p>
    <span>{{ publishedBooksMessage }}</span>
    <hr>
    <!-- Get -->
    <div>Name : {{ this.fullName }}</div>
    <!-- Set -->
    <div>이름 : {{ this.fullName = '길동 홍 ' }}</div>
  </div>
</template>