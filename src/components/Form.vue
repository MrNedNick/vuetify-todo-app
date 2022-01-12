<template>
  <v-container>
    <v-row class="d-flex">
      <v-text-field
        class="input"
        @keyup.enter="addTask"
        v-model="task"
        type="text"
        placeholder="Enter task"
      />
      <v-btn color="secondary" elevation="2" large outlined @click="addTask">
        SUBMIT
      </v-btn>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      task: "",
      tasks: [
        {
          name: "Clean my room",
        },
        {
          name: "Read new book",
        },
      ],
    };
  },

  methods: {
    addTask() {
      if(this.task.length === 0) return
      this.$emit("addTask", {
        name: this.task,
        id: new Date().getTime().toString()
      });

      this.task = ""
    },
  },
};
</script>

<style scoped>
.input {
  height: 42px;
  width: 300px;
  padding: 10px;
}
</style>