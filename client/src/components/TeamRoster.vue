<template>
  <div>
    <ul v-for="(player, index) in roster" :player="player" :key="index">
      <li>{{ player.Name }}</li>
    </ul>
  </div>
  <!-- <carousel-3d>
    <slide v-for="(player, i) in playerStats" :index="i" :key="i">
      <template slot-scope="{ index, isCurrent, leftIndex, rightIndex }">
        <img
          :data-index="index"
          :class="{
            current: isCurrent,
            onLeft: leftIndex >= 0,
            onRight: rightIndex >= 0,
          }"
          :src="player.Name"
          style="width: 75px; justify-content: center"
        />
      </template>
    </slide>
  </carousel-3d> -->
</template> 

<script>
export default {
  name: "team-roster",
  props: ["roster"],
};
</script>

<style>
</style>