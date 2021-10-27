<template>
  <div v-if="showAddTaskButton">
    <AddTask @add-task="newTask" />
  </div>

  <Tasks
    @toggle-reminder="toggleReminder"
    @delete-tas="deleteTask"
    :tasks="tasks"
  />
</template>
<script>
import Tasks from "../components/Tasks";
import AddTask from "../components/AddTask";

export default {
  name: "Home",
  components: {
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      //   showAddTaskButton: false,
    };
  },
  props: {
    showAddTaskButton: {
      type: Boolean,
    },
  },
  methods: {
    async toggleReminder(id) {
      const taskTotoggle = await this.fetchSingleTask(id);
      const currentState = {
        ...taskTotoggle,
        reminder: !taskTotoggle.reminder,
      };
      const res = await fetch(`api/tasks/${id}`, {
        method: "PUT",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(currentState),
      });
      const data = await res.json();
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: data.reminder } : task
      );
    },

    async newTask(task) {
      const res = await fetch("api/tasks", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(task),
      });
      const data = await res.json();

      this.tasks = [...this.tasks, data];
    },

    async deleteTask(id) {
      if (confirm("Comfirm task delete ?")) {
        const res = await fetch(`api/tasks/${id}`, {
          method: "DELETE",
        });

        res.status === 200
          ? (this.tasks = this.tasks.filter((task) => task.id !== id))
          : alert("Task doe not exist");
      }
    },
    async fetchTask() {
      const result = await fetch("api/tasks");

      const data = await result.json();
      return data;
    },
    async fetchSingleTask(id) {
      const res = await fetch(`api/tasks/${id}`);
      const data = await res.json();
      return data;
    },
  },

  async created() {
    this.tasks = await this.fetchTask();
  },
};
</script>
