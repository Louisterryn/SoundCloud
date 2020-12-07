<template>
  <div>
    <div v-for="musique in selectedMusique">
      {{ musique.titre }}
      {{ musique.son }}
      <button @click="deleteFavoris(index)">
        supp
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["selectedMusique"],
  data() {
    return {};
  },
  methods: {
    deleteFavoris(index) {}
  }
};
</script>

<style></style>
