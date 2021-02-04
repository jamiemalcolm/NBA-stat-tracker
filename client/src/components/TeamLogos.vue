<template>
  <div id="search-for-team">
    <div class="logo-container">
      <ul v-for="(team, index) in allTeams" :team="team" :key="index">
        <team-logo :team="team"></team-logo>
      </ul>
    </div>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import TeamLogo from "@/components/TeamLogo.vue";
import config from "@/config.js";
export default {
  data() {
    return {};
  },
  name: "team-logos",
  props: ["allTeams"],
  components: {
    "team-logo": TeamLogo,
  },
  methods: {
    showDetails: function () {
      eventBus.$emit("selected-team", this.team);
    },
  },
};
</script>

<style scoped>
.logo-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
}
li {
  list-style: none;
}
img {
  width: 75px;
}
</style>