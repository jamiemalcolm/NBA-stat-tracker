<template>
  <div id="app">
    <p>Welcome To Your NBA Stat Tracker</p>
    <team-logos :allTeams="allTeams"></team-logos>
    <team-details :team="selectedTeam"></team-details>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import config from "@/config.js";
import TeamLogos from "@/components/TeamLogos.vue";
import TeamDetails from "@/components/TeamDetails.vue";

export default {
  data() {
    return {
      allTeams: [],
      selectedTeam: {},
    };
  },
  mounted() {
    const api_key_1 = config.api_key_1;

    fetch(`https://api.sportsdata.io/v3/nba/scores/json/Teams?key=${api_key_1}`)
      .then((res) => res.json())
      .then((data) => (this.allTeams = data));

    eventBus.$on("selected-team", (team) => {
      this.selectedTeam = team;
    });
  },
  components: {
    "team-logos": TeamLogos,
    "team-details": TeamDetails,
  },
};
</script>

<style lang="css" scoped>
</style>