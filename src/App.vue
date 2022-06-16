<template>
  <div id="app" class="container">
    <Header :title="title" @show-add-task="showAddTask = !showAddTask" />
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";
export default {
  name: "App",
  components: { Header, Tasks, AddTask },
  data() {
    return {
      tasks: [],
      title: "task tracker",
      showAddTask: true,
    };
  },
  methods: {
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => {
        if (task.id === id) {
          return { ...task, reminder: !task.reminder };
        }
        return task;
      });
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    addTask(task) {
      const { date, text } = task;
      if (date !== "" && text !== "") {
        this.tasks = [...this.tasks, task];
      }
    },
  },
  created() {
    this.tasks = [
      {
        id: "1",
        text: "Doctors Appointment",
        day: "March 5th at 2:30pm",
        reminder: true,
      },
      {
        id: "2",
        text: "Meeting with boss",
        day: "March 6th at 1:30pm",
        reminder: true,
      },
      {
        id: "3",
        text: "Food shopping",
        day: "March 7th at 2:00pm",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
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
</style>
