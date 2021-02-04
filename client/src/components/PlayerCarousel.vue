<template>
  <div>
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
            style="width: 75px; justify-content: center"
          />
        </template>
      </slide>
    </carousel-3d>
  </div>
</template>

<script>
export default {};
</script>

<style>
</style>