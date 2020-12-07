<template>
  <div>
    <favoris v-show="favorisOn" :selectedMusique="selectedMusique" />
    <div v-for="(musique, index) in musiques" :key="index">
      {{ musique.titre }}
      {{ musique.son }}
      <button v-show="musique.test" @click="getFavoris(index)">
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
          test: "true"
        },
        {
          titre: "test1",
          son: "test1",
          test: "true"
        },
        {
          titre: "test2",
          son: "test2",
          test: "true"
        }
      ]
    };
  },
  methods: {
    getFavoris(index) {
      this.favorisOn = true;
      this.musiques[index].test = false;
      this.selectedMusique.push(this.musiques[index]);
      console.log(this.musiques[index].test);
    }
  }
};
</script>

<style></style>
