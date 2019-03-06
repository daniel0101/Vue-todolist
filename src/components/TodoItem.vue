<template>
    <div class="todo-item" :class="{'is-complete':item.completed}">
       <p>
           <input type="checkbox" :checked="item.completed" v-on:change="markComplete">
           {{ item.title }}
           <button @click="$emit('del-todo',item.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["item"],
    methods: {
        markComplete () {     
        //change state of completed --boolean       
          this.item.completed =  !this.item.completed;
        }
    }
}
</script>
<style>
    .todo-item {
        background: #F4F4F4;
        padding: 10px;
        border-bottom: 1px #CCC dotted;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .del{
        background: #FF0000;
        color: #FFF;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>


