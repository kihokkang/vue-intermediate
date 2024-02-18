<template>
  <div id="app">
    <BaseHeader></BaseHeader>
    <BaseInputbox></BaseInputbox>
    <BaseList></BaseList>
    <BaseFooter></BaseFooter>
  </div>
</template>

<script>
import BaseHeader from './components/BaseHeader.vue'
import BaseInputbox from './components/BaseInputbox.vue'
import BaseList from './components/BaseList.vue'
import BaseFooter from './components/BaseFooter.vue'

export default {
  // 컴포넌트 태그명은 첫글자를 대문자로 주로 정의한다(파스칼)
  components:{
    'BaseHeader': BaseHeader,
    'BaseInputbox': BaseInputbox,
    'BaseList': BaseList,
    'BaseFooter': BaseFooter
  }
}
</script>

<style>
body {
  text-align: center;
  background-color: #F6F6F6;
}
input {
  border-style: groove;
  width: 200px;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
