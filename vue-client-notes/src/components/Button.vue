<template>
<!--we are using v-bind: because we are passing a style-->
<!--@click can be used for events-->
    <button @click="onClick()" :style="{background: color}" class="btn">{{ text }}</button>
</template>

<script>
export default {
    name:'Button',
    props:{
        text: String,
        color: String,
    },
    methods:{
        onClick() {
            this.$emit('toggle-add-task')
        }
    }
}
</script>