<template>
    <ul>
        <li v-for="(todoList,index) in todoLists" v-bind:key="todoList.itme">
            <i class="fas fa-check checkIcon" v-bind:class="{checkBtnCompleted: todoList.completed}" v-on:click="toggleComplete(todoList, index)"></i>
            <span v-bind:class="{textCompleted: todoList.completed}">{{todoList.item}}</span>
            <span v-on:click="deleteTodo(todoList,index)"  class="icon">
                <i class="far fa-trash-alt"></i>
            </span>
        </li>
    </ul>
</template>

<script>
export default {
    data : function(){
        return {
            todoLists : []
            //value : obj {completed, item}
        }
    },
    created : function(){
        if(localStorage.length > 0){
            for(let i =0; i < localStorage.length; i++){
                if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
                    console.log(JSON.parse(localStorage.getItem(localStorage.key(i))));
                    this.todoLists.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
                }
            }
        }
    },
    methods : {
        deleteTodo : function(todoList,index){
            localStorage.removeItem(todoList.item);
            this.todoLists.splice(index,1);
        },
        toggleComplete : function(todoList){
            todoList.completed =! todoList.completed;
            //localstorage 갱신
            localStorage.removeItem(todoList.item);
            localStorage.setItem(todoList.item, JSON.stringify(todoList));
        }
    }
}
</script>

<style scoped>
ul {list-style-type: none; padding: 0; margin: 40px 0 0 0;}
li {margin: 0 0 20px 0; width: 100%; text-indent:15px; height: 50px; line-height: 50px; font-size:18px; font-weight: 300; background: #fff; border-radius: 5px;}
li .icon {float:right; margin: 0 15px 0 0; color: rgb(255, 238, 0);}
.textCompleted {text-decoration: line-through; color:#b3adad;}
.checkBtnCompleted {color: rgb(255, 238, 0);}
.checkIcon {margin:0 10px 0 0;}
</style>