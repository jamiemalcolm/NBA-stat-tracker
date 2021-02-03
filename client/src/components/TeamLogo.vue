<template>
  <img
    :src="team.WikipediaLogoUrl"
    :alt="team.Key"
    :value="team"
    @click="showDetails"
  />
</template>

<script>
import { eventBus } from "@/main.js";
export default {
  name: "team-logo",
  props: ["team"],
  methods: {
    showDetails: function () {
      eventBus.$emit("selected-team", this.team);
    },
  },
};
</script>

<style>
</style>