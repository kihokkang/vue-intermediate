<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="fa-solid fa-plus addBtn"></i>
        </span>

        <Modal v-if="showModal" @close="showModal = false">
            <h3 slot="header">
                경고!
                <i class="closeModalBtn fa-solid fa-xmark" @click="showModal = false"></i>
            </h3>
            <div slot="body">
                무언가를 입력하세요
            </div>
        </Modal>
    </div>
</template>

<script>
import Modal from './common/Modal.vue'
export default {
    data() {
        return {
            newTodoItem: "",
            showModal: false
        }
    },
    components: {
        Modal 
    },
    methods: {
        addTodo() {
            if (this.newTodoItem !== ''){
                this.$emit('addTodoItem', this.newTodoItem);
                this.clearInput();
            } else {
                this.showModal = !this.showModal;
            }  
        },
        clearInput() {
            // 저장하면 inputbox 초기화
            this.newTodoItem = '';
        }
    }

}
</script>

<style scoped>
input:focus {
    outline: none;
}
.inputBox {
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
}
.inputBox input {
    border-style: none;
    font-size: 0.9rem;
}
.addContainer {
    float:right;
    background: linear-gradient(to right, #6478fb,#8763fb);
    display: block;
    width: 3rem;
    border-radius: 0 5px 5px 0;
}
.addBtn{
    color: white;
    vertical-align: middle;
}
.closeModalBtn {
    color: #42b983
}

</style>