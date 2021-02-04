<template>
  <div>
    <img
      :src="team.WikipediaLogoUrl"
      :alt="team.Key"
      :value="team"
      @click="showDetails"
    />
  </div>
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
img {
  width: 75px;
}
</style>