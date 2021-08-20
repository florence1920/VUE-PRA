<template>
    <div class="deleteAll">
        <span v-on:click="deleteAll">
            CLEAR ALL
        </span>
    </div>
</template>

<script>
export default {
    methods :{
        deleteAll : function(){
            localStorage.clear();
        }
    }
}
</script>

<style>
    .deleteAll{height: 50px; line-height: 50px; width: 100px; margin: 0 auto; text-align: center; background: #fff;}
</style>