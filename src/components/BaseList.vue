<template>
  <div>
    <transition-group name="list" tag="ul">
      <li v-for="(todoItems, index) in propsdata" v-bind:key="todoItems.item" class="shadow">
        <i class="checkBtn fa-solid fa-check" v-bind:class="{checkBtnCompleted: todoItems.completed}" 
          v-on:click="toggleComplete(todoItems, index)">
        </i>
        <span v-bind:class="{textCompleted: todoItems.completed}">{{ todoItems.item }}</span>
        <span class="removeBtn" v-on:click="removeTodo(todoItems, index)">
          <i class="fa-solid fa-trash"></i>
        </span>
      </li>
    </transition-group>
  </div>
</template>

<script>
export default {
  props : ['propsdata'],
  methods: {
    removeTodo(todoItem, index) {
      this.$emit('removeItem', todoItem, index);
    },
    toggleComplete(todoItem, index) {
      this.$emit('toggleItem', todoItem, index);
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

/* 리스트 아이템 트랜지션 효과 */
.list-enter-active, .list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}
</style>