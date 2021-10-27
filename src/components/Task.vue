<template>
  <div @draggable="true" 
    @dblclick="$emit('togglerem', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <!-- //@dblclick="$emit('toggle-reminder', task.id)" -->
    <div class="test">
      <h3>
        {{ task.text }}
        <i class="fas fa-times"></i>
      </h3>
      <i @click="$emit('delete-task', task.id)"> x </i>
    </div>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>

export default {
  name: "Task",
  props: {
    task: Object,
  }
};
</script>

<style scoped>
.task {
  padding: 0px 30px;
  /* padding-left: 50px; */
  border: 1px solid green;
  /* background-color:gray; */
  border-radius: 5px;
  margin-top: 20px;
  cursor: move;
}
h3 {
  display: flex;
}
.test {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
i {
  color: red;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  font-size: 20px;
  cursor: pointer;
}
.reminder {
  border-left: 10px solid green;
}
</style>
