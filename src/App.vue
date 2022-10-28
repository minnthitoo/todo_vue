<template>
  <div class="">
    <div class="container">
      <h1 class="text-center bg-primary text-white p-3">
        {{ name }}'ToDo List
      </h1>
      <div class="container">
        <div class="row mt-3">
          <div class="col">
            <input type="text" name="" class="form-control" id="" v-model="newTask" v-on:keyup.enter="addTask()">
          </div>
          <div class="col">
            <button class="btn btn-secondary" @click="addTask()">Add</button>
          </div>
        </div>
        <div class="row my-4">
          <div class="col">Tasks</div>
          <div class="col-2">Done</div>
        </div>
        <div class="row" v-for="(task, index) in filterTask" v-bind:key="index">
          <div class="col" :class="task.done ? 'delete' : ''">
            {{ task.actions }}
          </div>
          <div class="col-2">
            <input type="checkbox" v-model="task.done" />
          </div>
        </div>
        <div class="row bg-danger text-center text-white p-2">
          <h5>Hide Completed tasks</h5>
          <input type="checkbox" v-model="hideCompleted" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    name: "Minn Thit Oo",
    hideCompleted : false,
    newTask : '',
    tasks: [
      {
        actions: "By new phone",
        done: false,
      },
      {
        actions: "By new Shoe",
        done: true,
      },
      {
        actions: "call to Si Thu Aung",
        done: false,
      },
      {
        actions: "By new shirt",
        done: true,
      },
    ],

  }),
  computed : {
      filterTask(){
        return this.hideCompleted ? this.tasks.filter((v)=> !v.done) : this.tasks;
      }
    },
  methods : {
    addTask(){
      if(this.newTask === ''){
        alert("Enter task");
      }else{
        this.tasks.push({actions : this.newTask, done : false});
        this.newTask = '';
      }
    }
  }

};
</script>
<style>
.delete {
  text-decoration: line-through;
}
</style>
