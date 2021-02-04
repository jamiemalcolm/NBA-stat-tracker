<template>
  <div id="app">
    <p>Welcome To Your NBA Stat Tracker</p>
    <div class="roster-container">
      <team-roster :roster="playerStats"></team-roster>
    </div>
    <team-logos :allTeams="allTeams"></team-logos>
    <div v-if="selectedTeam">
      <team-details :team="selectedTeam"></team-details>
    </div>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import config from "@/config.js";
import TeamLogos from "@/components/TeamLogos.vue";
import TeamDetails from "@/components/TeamDetails.vue";
import TeamRoster from "@/components/TeamRoster.vue";

export default {
  data() {
    return {
      allTeams: [],
      selectedTeam: null,
      playerStats: {},
    };
  },
  methods: {},
  mounted() {
    const api_key_1 = config.api_key_1;

    fetch(`https://api.sportsdata.io/v3/nba/scores/json/Teams?key=${api_key_1}`)
      .then((res) => res.json())
      .then((data) => (this.allTeams = data));

    eventBus.$on("selected-team", (team) => {
      this.selectedTeam = team;
    });

    eventBus.$on("players-request", () => {
      let teamKey = this.selectedTeam.Key;
      fetch(
        `https://api.sportsdata.io/v3/nba/stats/json/PlayerSeasonStatsByTeam/2020/${teamKey}?key=${api_key_1}`
      )
        .then((res) => res.json())
        .then((data) => (this.playerStats = data));
    });
  },
  components: {
    "team-logos": TeamLogos,
    "team-details": TeamDetails,
    "team-roster": TeamRoster,
  },
};
</script>

<style lang="css" scoped>
.roster-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>