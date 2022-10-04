<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <div class="event-card">
      <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
      <p>{{ event.description }}</p>
    </div>
  </div>
</template>

<script>
import EventService from "@/services/EventService";

export default {
  data() {
    return {
      event: null,
    };
  },
  props: ["id"],
  created() {
    EventService.getEvent(this.id)
      .then((response) => {
        this.event = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
<style scoped></style>
