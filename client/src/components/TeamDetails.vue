<template>
  <div v-if="team">
    <p>{{ team.City }}</p>
    <p>{{ team.Name }}</p>
  </div>
</template>

<script>
export default {
  name: "team-details",
  props: ["team"],
};
</script>

<style>
</style>