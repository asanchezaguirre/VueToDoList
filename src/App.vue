<template>
  <div class="container">
    <h1>{{ name }}´s awesome to do app!</h1>
      <form-task @addTask = "addTask"/>
   
    <hr />
    <h2>Pending tasks</h2>
    <todo-list @toggle = "toggle" :list="pendingTasks"/>

    <hr />

    <h2>Completed tasks</h2>
     <todo-list @toggle = "toggle" :list="completedTasks"/>
  </div>
  

  
</template>

<script>
import todoList from './components/todoList'
import formTask from './components/formTask'
export default {
  components:{
    todoList,
    formTask
  },
  data(){
    return{
      name: "Adriana",
      newTask: "",
      list: [
        {label: "Learn Vue", done: true},
        {label: 'Create To do', done: false},
        {label: 'Deploy', done: false},
        {label: 'Go for a drink', done: false},
        {label: 'Learn', done: false},
      ]
    };
  },
  methods:{
    addTask(newTask){
      if (!newTask){
        return;
      }
      this.list.push({ label: newTask, done:false});

    },
    toggle (item){
      item.done = !item.done;
    }
  },
  computed: {
    completedTasks(){
      return this.list.filter(item => item.done)
    },
    pendingTasks(){
      return this.list.filter(item => !item.done)
    }
  }
  
};

</script>