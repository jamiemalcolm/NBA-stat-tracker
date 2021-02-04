<template>
  <div v-if="team">
    <p>{{ team.City }}, {{ team.Name }}</p>
    <p>Conference: {{ team.Conference }}</p>
    <p>Division: {{ team.Division }}</p>
    <button class="getPlayers" @click="getPlayers">Get Players</button>
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
</style>