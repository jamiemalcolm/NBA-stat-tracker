<template>
  <img :src="team.WikipediaLogoUrl" :alt="team.Key" />
</template>

<script>
export default {
  name: "team-logo",
  props: ["team"],
};
</script>

<style>
</style>