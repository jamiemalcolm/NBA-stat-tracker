<template>
  <div id="search-for-team">
    <div class="logo-container">
      <carousel-3d>
        <slide v-for="(team, i) in allTeams" :index="i" :key="i">
          <template slot-scope="{ index, isCurrent, leftIndex, rightIndex }">
            <img
              :data-index="index"
              :class="{
                current: isCurrent,
                onLeft: leftIndex >= 0,
                onRight: rightIndex >= 0,
              }"
              :src="team.WikipediaLogoUrl"     
            />
          </template>
        </slide>
      </carousel-3d>

      <!-- <ul v-for="(team, index) in allTeams" :team="team" :key="index">
        <team-logo :team="team"></team-logo> -->
      </ul>
    </div>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import TeamLogo from "@/components/TeamLogo.vue";
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