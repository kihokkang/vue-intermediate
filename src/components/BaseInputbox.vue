<template>
    <div>
        <input type="text" v-model="newTodoItem">
        <button v-on:click="addTodo">add</button>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            newTodoItem: ""
        }
    },
    methods: {
        addTodo: function() {
            console.log('addTodo ::', this.newTodoItem)
            
            localStorage.setItem(this.newTodoItem, this.newTodoItem)
            // 저장하면 inputbox 초기화
            this.newTodoItem = '';

        }
    }

}
</script>

<style>

</style>