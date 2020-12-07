<template>
  <div>
    <favoris v-show="favorisOn" :testArray="testArray" />
    <div v-for="(musique, index) in musiques" :key="index">
      {{ musique.titre }}
      {{ musique.son }}
      <button @click="getFavoris(index)">favoris</button>
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
      selectedMusique: "",
      testArray: [""],
      musiques: [
        {
          titre: "cc",
          son: "tt",
          test: "false"
        },
        {
          titre: "test1",
          son: "test1",
          test: "false"
        },
        {
          titre: "test2",
          son: "test2",
          test: "false"
        }
      ]
    };
  },
  methods: {
    getFavoris(index) {
      this.favorisOn = true;
      this.selectedMusique = this.musiques[index];

      this.testArray.push(this.selectedMusique);
    }
  }
};
</script>

<style></style>
