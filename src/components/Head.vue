<template>
  <div class="main"> 
    <h1>{{title}}</h1>
    <Button v-show="homePage" @toggle-add-task-button="$emit('toggle-add-task-button')" :text="showTask ? 'Close' : 'Add Task'" :color="showTask ? 'red' : 'green'"/>
  </div>
</template>

<script>
import Button from './Button';
export default {
  name: "Head",
  components: {
    Button,
  },
  props: {
    title: {
      type: String,
      default: "My World",
    },
    showTask:{
      type: Boolean,
    }
   
  },
  computed:{
    homePage(){
      return this.$route.path === '/'? true : false;
    }
  }
};
</script>

<style scoped>
    div {
    display: flex;
    justify-content: space-between;
    align-items:center;
}
</style>
