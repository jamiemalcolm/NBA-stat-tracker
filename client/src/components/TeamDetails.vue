<template>
  <div class="team-details">
    <p>{{ team.City }}, {{ team.Name }}</p>
    <p>Conference: {{ team.Conference }}</p>
    <p>Division: {{ team.Division }}</p>
    <button
      class="getPlayers"
      @click="getPlayers"
      v-scroll-to="{ element: '.roster-container', easing: 'linear' }"
    >
      Get Players
    </button>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";

export default {
  name: "team-details",
  props: ["team"],
  methods: {
    getPlayers: function () {
      eventBus.$emit("players-request");
    },
  },
};
</script>

<style>
li {
  list-style-type: none;
}
</style>