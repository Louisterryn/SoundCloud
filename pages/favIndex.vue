<template>
  <div class="mainContainer">
    <favoris
      v-show="favorisOn"
      :selectedMusique="selectedMusique"
      class="componsantFavoris"
    />
    <h1>Liste musique</h1>
    <div class="mainFavoris" v-for="(musique, index) in musiques" :key="index">
      Titre : {{ musique.titre }} Son :{{ musique.son }}
      <button v-show="musique.afficher" @click="getFavoris(index)">
        favoris
      </button>
    </div>
  </div>
</template>

<script>
import favoris from "@/components/favoris";
export default {
  components: {
    favoris
  },
  data() {
    return {
      favorisOn: false,
      selectedMusique: [],
      musiques: [
        {
          titre: "cc",
          son: "tt",
          afficher: "true"
        },
        {
          titre: "test1",
          son: "test1",
          afficher: "true"
        },
        {
          titre: "test2",
          son: "test2",
          afficher: "true"
        }
      ]
    };
  },
  methods: {
    getFavoris(index) {
      this.favorisOn = true;
      this.musiques[index].afficher = false;
      this.selectedMusique.push(this.musiques[index]);
      console.log(this.musiques[index].afficher);
    }
  }
};
</script>

<style>
.componsantFavoris {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
</style>
