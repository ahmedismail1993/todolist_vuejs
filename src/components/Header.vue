<template>
    <header>
      <h1>{{title}}</h1>
      <Button @click-btn="$emit('show-add-task')" 
              :text="showAddTask ? 'Close' : 'Add Task'"
              :color="showAddTask ? 'red' : 'green'"/>
    </header>
</template>

<script>
  import Button from './Button.vue'
    export default {
        name:'Header',
        components:{
            Button
        },
        props:{
            showAddTask:Boolean,
            title:String,
        }
    }
</script>

<style  scoped>
header{
    display:flex;
    justify-content: space-between;
    align-items: center;
}

</style>