<template>
    <ul>
        <li v-for="todoList in todoLists" v-bind:key="todoList.itme">
            {{todoList.item}}
            <span>
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
        }
    },
    created : function(){
        if(localStorage.length > 0){
            for(let i =0; i < localStorage.length; i++){
                if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
                    this.todoLists.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
                }
            }
        }
    }
}
</script>

<style scoped>
ul {list-style-type: none; padding: 0; margin: 40px 0 0 0;}
li {margin: 0 0 20px 0; width: 100%; text-indent:15px; height: 50px; line-height: 50px; font-size:18px; font-weight: 300; background: #fff; border-radius: 5px;}
li span {float:right; margin: 0 15px 0 0; color: rgb(255, 238, 0);}
</style>