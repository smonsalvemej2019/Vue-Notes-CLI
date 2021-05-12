<template>
<div>
<!--the v-for directive will loop trough the array-->
    <div v-for="task in tasks" :key="task.id">
        <!--we are going to emmit one more level higher to the app file where we have access to the data-->
        <Task @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task',task.id)" :task="task"/>
    </diV>
</div>
</template>

<script>
import Task from './Task'

export default {
    name: 'Tasks',
    props:{
        tasks: Array,
    },
    components:{
        Task
    },
    emits:['delete-task','toggle-reminder'],
}
</script>