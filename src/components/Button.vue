<template>
  <button :style="{background: color}" @click="onClick()" id="btn">{{text}}</button>
</template>

<script>
export default {
    name: 'Button',
    props:{
        text: String,
        color: String,
    },
    methods: {
        onClick(){
            this.$emit('btn-click');
        }
    },
}
</script>

<style scoped>
    button{
        border: none;
        width: max-content;
        height: 30px;
        border-radius: 3px;
        color: white;
        font-weight: bolder;
        transition: 0.5s;
    }

    button:hover{
        filter: brightness(120%);
        cursor: pointer;
    }
</style>