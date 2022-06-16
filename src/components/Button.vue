<template>
    <button  @click="toggleShowTask()"  :style="{background: color}" class="btn">
       {{text}}
    </button>
</template>

<script>
    export default {
        name:'Button',
        props:{
            color:String,
            text:String
        },
        methods:{
            toggleShowTask(){
                this.$emit('click-btn')
            }
        }
    }
</script>

<style scoped>

</style>