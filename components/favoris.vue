<template>
  <div>
    <div v-for="musique in testArray">
      {{ musique.titre }}
      {{ musique.son }}
    </div>
  </div>
</template>

<script>
export default {
  props: ["testArray"],
  data() {
    return {};
  },
  methods: {}
};
</script>

<style></style>
