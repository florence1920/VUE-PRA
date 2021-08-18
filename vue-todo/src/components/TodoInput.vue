<template>
    <div class="inputWrap">
        <input type="text" v-model="todoInput" v-on:keyup.enter="inputDo">
        <span v-on:click="inputDo" class="plusBtn">
            <i class="fas fa-plus"></i>
        </span>
    </div>
</template>

<script>
export default {
    data: function(){
        return {
            todoInput : '',
        }
    },
    methods: {
        inputDo : function(){
            if(this.todoInput !== ''){
                let obj = {completed:false, item:this.todoInput};
                localStorage.setItem(this.todoInput,JSON.stringify(obj));
                this.clearInput();
            }
        },
        clearInput : function(){
            this.todoInput = '';
        }
    }
}
</script>

<style scoped>
    
    input {padding: 0 0 0 15px; width: 95%; height: 50px; line-height: 50px; border-radius: 5px; border:none; font-size: 15px;}
    input:focus {outline: none;}
    .plusBtn {width: 5%; padding: 0 0 0 10px; color: #fff; cursor: pointer;}
</style>