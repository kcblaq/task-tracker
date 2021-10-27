<template>
  <div>
    <button class="btn" :style="{background: color}" @click="myFunc()">{{ text }}</button>
  </div>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: {
      type: String,
      default: "Add Task",
    },
    color:{
        type: String,
        default: "green"
    }
  },
  methods: {
      myFunc() {
          this.$emit('toggle-add-task-button')
      }
  },
};
</script>

<style scoped>
.btn {
  padding: 10px;
  border-radius: 10px;
  color: white;
  border-block-end-color: blue;
}
</style>
