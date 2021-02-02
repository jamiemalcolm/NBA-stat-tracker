<template>
  <div id="search-for-team">
    <div class="logo-container">
      <ul v-for="(team, index) in allTeams" :team="team" :key="index">
        <li>
          <img
            :src="team.WikipediaLogoUrl"
            :alt="team.Key"
            v-bind="team"
            @click="showDetails"
          />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
export default {
  data() {
    return {};
  },
  props: ["allTeams"],
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