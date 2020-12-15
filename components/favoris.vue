<template>
  <div>
    <div v-for="musique in selectedMusique">
      <ul>
        <li>Titre : {{ musique.Titre }} Son :{{ musique.Artiste }}</li>
      </ul>
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

<style>
li {
  color: white;
}
</style>
