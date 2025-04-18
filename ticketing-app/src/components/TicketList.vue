<template>
  <div>
    <h2>Ticket List</h2>
    <ul>
      <li v-for="ticket in tickets" :key="ticket.id">
        <strong>{{ ticket.problemDescription }}</strong><br />
        GitLab URL: <a :href="ticket.gitLabURL" target="_blank">{{ ticket.gitLabURL }}</a><br />
        Assignees: {{ ticket.assignees.join(", ") }}<br />
        Status: {{ ticket.status }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tickets: [],
    };
  },
  created() {
    fetch("/data/tickets.json")
      .then((response) => response.json())
      .then((data) => {
        this.tickets = data;
      });
  },
};
</script>
