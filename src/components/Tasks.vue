<template>
  <div
    v-for="task in tasks"
    :key="task.id"
  >
    <Task
      @togglerem="$emit('toggle-reminder', task.id)"
      @delete-task="$emit('delete-tas', task.id)"
      :task="task"
    />
  </div>
</template>

<script>
import Task from "./Task";
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
  emits: ["delete-tas", "toggle-reminder"],
  methods: {
    handleDragStart(e) {
      e.preventDefault();
      console.log("Miss me!");
    },
  },
};
</script>

<style scoped></style>
