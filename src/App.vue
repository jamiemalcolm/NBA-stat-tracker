<template>
  <div id="app">
    <p>Welcome To Your NBA Stat Tracker</p>
  </div>
</template>

<script>
import config from "@/config.js";
export default {
  data() {
    return {
      allTeams: [],
    };
  },
  mounted() {
    const api_key_1 = config.api_key_1;

    fetch(
      `https://api.sportsdata.io/v3/nba/scores/json/AllTeams?key=${api_key_1}`
    )
      .then((res) => res.json())
      .then((data) => (this.allTeams = data));
  },
};
</script>

<style>
</style>