<template>
  <div id="app">
<h3>{{ title }}</h3>

<tasks :tasks="tasks" v-on:completeTaskEvent="completeTheTask" v-on:deletetaskEvent="deleteTheTask"></tasks>
<input type="text" class="form-control mb-2" v-model="newTask">
<input type="button" class="form-control mb-2 btn btn-success btn-block" value="add" v-on:click="addnew"> 
  </div>
</template>

<script>
import tasks from './components/tasks'
export default {
  name: 'App',
  components: {
    tasks
  },
  data() {
    return {
      title: 'First Tasks App',
      newTask: null,
      tasks: [
        {
          body: 'Go to home',
          completed: false
        },
            {
          body: 'Go to work',
          completed: false
        },
            {
          body: 'Go to School',
          completed: false
        }
      ]
    }
  },
  methods:{
addnew() {
this.tasks.push({
   body: this.newTask,
   completed: false
});
this.newTask = null
},
completeTheTask(task){
  task.completed = !task.completed
},
deleteTheTask(index){
  console.log('deleted' +index)
  this.tasks.splice(index, 1);
}
}


}
</script>

<style>
#app {
  margin-top: 60px;
}
.card {
  padding: 20px;
  background: #eee;
}
</style>
