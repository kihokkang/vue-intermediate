<template>
  <div id="app">
    <BaseHeader></BaseHeader>
    <BaseInputbox v-on:addTodoItem="addOneItem"></BaseInputbox>
    <BaseList :propsdata="todoItems" 
      v-on:removeItem="removeOneItem" 
      v-on:toggleItem="toggleOneItem"></BaseList>
    <BaseFooter v-on:clearAll="clearAllItems"></BaseFooter>
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
  },
  data: function() {
    return {
      todoItems:[]
    }
  },
  methods: {
    addOneItem: function(todoItem) {
      const obj = {completed: false, item: todoItem}
      localStorage.setItem(todoItem, JSON.stringify(obj));
      this.todoItems.push(obj);
    },
    removeOneItem : function(todoItem, index) {
      localStorage.removeItem(todoItem.item);
      this.todoItems.splice(index, 1);
    },
    toggleOneItem: function(todoItem, index) {
      this.todoItems[index].completed = !this.todoItems[index].completed;
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    },
    clearAllItems: function() {
      this.todoItems = [];
      localStorage.clear();
    }
  },
  created: function() {
    if(localStorage.length > 0){
      for(let i = 0; i < localStorage.length; i++){
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
          this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))))
        }      
      }
    }
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
