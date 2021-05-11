<!--the html for this component-->
<template>
    <header>
        <h1>{{ title }}</h1>
    </header>
</template>
<!--we are exporting this template so it can be mounted by the app.vue-->
<script>
export default {
    name: 'Header',
    props: {
        //from the app.vu we are passing a prop called title
        //the title is a type string with a default value
        //if we get rid of the prop in app.js, it will display default
        title:{
            type: String,
            default: 'Hello World'
        }
    },
}
</script>
<!--style is going to be scoped for this component only-->
<style scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>

