<template>
  <div>
    <h1>{{part.title}}</h1>
    <div>{{part.description}}</div>
  </div>
</template>

<script>

export default {
  name: "PartInfo",
  parts: {},
  computed: {
    part() {
      const { partType, id } = this.$route.params;

      return parts[partType].find(part => part.id === +id);
    }
  },
  mounted () {
    axios
    .get('https://angry-babbage-98ec47.netlify.com/.netlify/functions/partlist')
    .then(response => {
      this.availableParts = response.data;
    });
  }
};
</script>

<style>
</style>
