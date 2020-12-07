<template>
  <div>
    <div v-for="musique in selectedMusique">
      Titre : {{ musique.titre }} Son :{{ musique.son }}
    </div>
  </div>
</template>

<script>
export default {
  props: ["selectedMusique"],
  data() {
    return {};
  },
  methods: {}
};
</script>

<style></style>
