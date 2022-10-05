<template>
  <h1>Events for good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventService from "@/services/EventService";
import EventCard from "@/components/EventCard";

export default {
  name: "Home",
  components: {
    EventCard,
  },
  prop: ['page'],
  data() {
    return {
      events: null,
    };
  },
  created() {
    EventService.getEvents(2, this.page)
      .then((response) => {
        this.events = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
