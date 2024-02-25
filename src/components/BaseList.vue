<template>
  <div>
    <ul>
      <li v-for="(todoItems, index) in todoItems" v-bind:key="todoItems.item" class="shadow">
        <i class="checkBtn fa-solid fa-check" v-bind:class="{checkBtnCompleted: todoItems.completed}" 
          v-on:click="toggleComplete(todoItems, index)">
        </i>
        <span v-bind:class="{textCompleted: todoItems.completed}">{{ todoItems.item }}</span>
        <span class="removeBtn" v-on:click="removeTodo(todoItems, index)">
          <i class="fa-solid fa-trash"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      todoItems:[]
    }
  },
  methods: {
    removeTodo: function(todoItem, index) {
      console.log('clicked removeTodo :: ', todoItem + ' ' + index);
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index,1);

    },
    toggleComplete: function(todoItem, index) {
      todoItem.completed = !todoItem.completed;
      // 로컬 스토리지의 데이터를 갱신
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    }
  },
  created: function() {
    if(localStorage.length > 0){
      for(var i = 0; i < localStorage.length; i++){
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
          this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))))
        }      
      }
    }
  }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  padding-top: 0;
  text-align: left;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
.removeBtn {
  margin-left: auto;
  color: #de4343
}
.checkBtn {
  line-height: 45px;
  color:#62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color:#b3adad
}
</style>