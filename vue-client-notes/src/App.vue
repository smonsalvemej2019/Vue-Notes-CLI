<template>
  <div class="container">
    <!--we have a component called Header-->
    <!--we can pass props into our components-->
    <!--ex we can pass a title with the value Task Tracker-->
  <Header title="Task Tracker"/>
  <!--we are passing an array of dynamic data called tasks-->
  <!--we emitted from the lower level task file -> tasks file -> app file-->
  <!--the app file has access to the data and is able to change it by callinhg deleteTask method-->
  <Tasks
  @toggle-reminder ="toggleReminder"
  @delete-task="deleteTask"
  :tasks="tasks" />
  </div>
</template>

<script>
//first we import our components...
import Header from './components/Header'
import Tasks from './components/Tasks'

export default {
  name: 'App',
  components: {
    //...then register them in the export
    Header,
    Tasks,
  },
  data() {
    //returns the tasks data array
    return{
      tasks: []
      }
    },
    methods:{
      deleteTask(id) { //will filter out the task we want with the the fileter method
        if (confirm('Are you sure?')){
        //will return all the tasks with an id NOT EQUALS to the passed id
        //this function is reinitializing the array
        this.tasks = this.tasks.filter((task)=> task.id !== id)
        }
      },

      toggleReminder(id){
        this.tasks= this.tasks.map((task)=> task.id === id ? {...task, reminder: !task.reminder} : task)
      }
    },
    created() {
      //initializes the array
      this.tasks = [
      {
        id: 1,
        text: 'Doctors Appointment',
        day: 'March 1st at 2:30pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'Meeting at school',
        day: 'March 3rd at 1:30pm',
        reminder: true,
      },
      {
        id: 3,
        text: 'Food Shopping',
        day: 'March 3rd at 11:00am',
        reminder: false,
      }
      ]
    }
  }

</script>

<style>
/*this style is global*/
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
