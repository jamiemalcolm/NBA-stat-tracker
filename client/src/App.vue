<template>
  <div id="app">
    <p>Welcome To Your NBA Stat Tracker</p>
    <team-logo :allTeams="allTeams"></team-logo>
  </div>
</template>

<script>
import config from "@/config.js";
import TeamLogo from "@/components/TeamLogo.vue";
import TeamDetails from "@/components/TeamDetails.vue";
import eventBus from "@/main.js";
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
    "team-logo": TeamLogo,
    "team-details": TeamDetails,
  },
};
</script>

<style lang="css" scoped>
#app {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
}
</style>