<template>
  <div class="app">
    <div class="container">
      <Header />
      <div class="actions">
        <Button description="Create Task" action="create" />
      </div>
      <div class="task_container">
        <div class="options"></div>
        <div class="tasks">
          <div v-for="task in tasks" :key="task.id">
            <Task @do-task="doTask" :task="task" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Button from "./components/Button.vue";
import Task from "./components/Task.vue";

export default {
  name: "App",
  components: {
    Header,
    Button,
    Task,
  },
  data() {
    return {
      tasks: [],
      totalTasks: 0,
      doneTasks: [],
    };
  },
  methods: {
    doTask(id) {
      let index = this.tasks.map((task) => task.id).indexOf(id);
      if (index >= 0) {
        this.tasks[index].done = true;
        this.doneTasks.push(this.tasks[index]);
        this.tasks.splice(index, 1);
        this.totalTasks = this.tasks.length;
      }

      if (index < 0) {
        index = this.doneTasks.map((task) => task.id).indexOf(id);
        this.doneTasks[index].done = false;
        this.tasks.push(this.doneTasks[index]);
        this.doneTasks.splice(index, 1);

        this.totalTasks = this.tasks.length;
      }
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        desc: "Buy new notepad - Younote",
        day: "03/07/2021 - 14pm",
        done: false,
      },
      {
        id: 2,
        desc: "VueJs  - Vue Router",
        day: "05/07/2021 - 17pm",
        done: false,
      },
      {
        id: 3,
        desc: "Buy food- For the month",
        day: "07/07/2021 - 12pm",
        done: false,
      },
    ];

    this.totalTasks = this.tasks.length;
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  height: 100vh;
}

#app .container {
  width: 100vw;
  height: 100vh;
  background-color: #a190b2;

  display: flex;
  flex-direction: column;
  align-items: center;
}

#app .container .actions {
  padding-top: 3em;
  width: 100%;
  height: 20%;

  display: flex;
  justify-content: center;
}

#app .container .task_container {
  width: 100%;
  height: 65%;
  background-color: #eeeeee;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;

  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

#app .container .task_container .tasks {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

#app .container .task_container .tasks span {
  width: 100%;
  height: 10%;

  font-weight: bolder;
  color: #a190b2;
  font-size: 1.5em;

  margin-bottom: 1em;
}

#app .container .task_container .done_tasks {
  width: 70%;
}

#app .container .task_container .done_tasks span {
  width: 100%;
  height: 10%;

  font-weight: bolder;
  color: #a190b2;
  font-size: 1.5em;

  margin-bottom: 1em;
  margin-left: 1em;
}
</style>
