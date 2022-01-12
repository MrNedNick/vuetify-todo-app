<template>
  <div class="container">
    <div class="task">
      <h3>{{ task.name }}</h3>
      <v-checkbox
      class="checkbox"
      v-model="checked"
      @change="$emit('change', $event)" />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      requaired: true,
    },
  },
  data() {
    return {
      checked: false,
    };
  },
};
</script>

<style >
.container {
  display: flex;
  justify-content: center;
}
.task {
  display: flex;
  justify-content: space-between;
  width: 400px;
}
h3 {
  display: flex;
  justify-content: center;
  flex-direction: column;
  margin: 0;
  padding: 0;
}
.checkbox {
  margin: 0;
  padding: 0;
}
</style>




