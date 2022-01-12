<template>
  <div class="main">
    {{ tasks }}
    {{ checked }}
    {{ arr }}
    <Logo />
    <Form @addTask="addTask" />
    <Task
      v-for="(task, id) in tasks"
      :task="task"
      :key="id"
      @change="isShown(task.id, $event)"
    />
    <div v-if="btnStatus"><Delete @deleteTask="deleteTask" /></div>
    <div v-else></div>
    ``
  </div>
</template>

<script>
import Logo from "./components/Logo.vue";
import Form from "./components/Form.vue";
import Task from "./components/Task.vue";
import Delete from "./components/Delete.vue";

export default {
  name: "App",
  components: {
    Logo,
    Form,
    Task,
    Delete,
  },
  data: () => ({
    checked: [],
    btnStatus: false,
    arr: [],
    task: "",
    tasks: [
      { name: "Clean my room", id: 1 },
      { name: "Read new book", id: 2 },
    ],
  }),

  methods: {
    addTask(name) {
      this.tasks.push(name);
    },
    deleteTask() {},
    isShown(id, value) {
      console.log(id, value);
      if (value === true) {
        this.btnStatus = true;
        this.checked.push(id);
      }
      this.checked - this.checked.filter(function(item, pos) {
          return this.checked.indexOf(item) == pos;})
      }
    }
}
</script>

<style scoped>
</style>


