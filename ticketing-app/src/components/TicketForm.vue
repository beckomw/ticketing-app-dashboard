<template>
  <form @submit.prevent="addTicket">
    <input v-model="problemDescription" placeholder="Problem Description" required />
    <input v-model="gitLabURL" placeholder="GitLab URL" required />
    <input v-model="assignees" placeholder="Assignees (comma-separated)" required />
    <button type="submit">Add Ticket</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      problemDescription: "",
      gitLabURL: "",
      assignees: "",
    };
  },
  methods: {
    addTicket() {
      const newTicket = {
        id: Date.now(),
        problemDescription: this.problemDescription,
        gitLabURL: this.gitLabURL,
        assignees: this.assignees.split(","),
        status: "Open",
      };

      fetch("/data/tickets.json", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(newTicket),
      });

      // Reset fields
      this.problemDescription = "";
      this.gitLabURL = "";
      this.assignees = "";
    },
  },
};
</script>
