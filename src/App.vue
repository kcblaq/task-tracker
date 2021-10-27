<template>
  <div class="container">
    <Head
      title="Task Tracker"
      @toggle-add-task-button="toggleAddTaskBtn"
      :showTask="showAddTaskButton"
    />
    
    <router-view :showAddTaskButton="showAddTaskButton"></router-view>
   <Footer /> 
  </div>
</template>

<script>
// import { ref } from 'vue';     
import Head from "./components/Head";

import Footer from "./components/Footer";


export default {
  name: "App",



  components: {
    Head,
    Footer
  },

  data() {
    return {
    
      showAddTaskButton: false,
    };
  },

  methods: {
    toggleAddTaskBtn() {
      this.showAddTaskButton = !this.showAddTaskButton;
    },
   


  },

 
};
</script>

<style scoped>

.container {
  width: 50%;
  min-height: 100px;
  border: 1px solid black;
  border-radius: 7px;
  padding: 1.2rem;
  margin: 0;
  box-shadow: filter(2px 2px 2 rgba(29, 27, 29, 0.1));
  filter: drop-shadow(2px 2px 2px rgba(255, 122, 255, 0.1));
}
</style>
