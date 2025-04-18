<template>
  <div>
    <h1>Team Ticketing App</h1>
    <TicketForm />
    <TicketList />
  </div>
</template>

<script>
import TicketForm from "../components/TicketForm.vue";
import TicketList from "../components/TicketList.vue";

export default {
  components: {
    TicketForm,
    TicketList,
  },
};
</script>
