<template>
  <form>
    <label for="name">Fan name:</label>
    <input type="text" id="name" v-model="name" />

    <br />

    <label for="arc">Favorite arc:</label>
    <select id="arc" v-model="favoriteArc">
      <option v-for="arc in arcs" :key="arc.value" :value="arc.value">
        {{ arc.label }}
      </option>
    </select>

    <br />

    <label for="characters">Favorite characters:</label>
    <input
      type="text"
      id="characters"
      v-model="favoriteCharacter"
      @keyup="handleKeyUp"
    />
    <small>Write characters separated by commas (,)</small>
    <ul>
      <li v-for="character in favoriteCharacters" :key="character">
        <button type="button" @click="deleteCharacter(character)">
          {{ character }}
        </button>
      </li>
    </ul>

    <ul>
      <li>Fan name: {{ name }}</li>
      <li>Favorite arc: {{ favoriteArc }}</li>
      <li>Favorite characters: {{ favoriteCharacters }}</li>
    </ul>
  </form>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      arcs: [
        { label: "Hunter Exam", value: "hunter-exam" },
        { label: "Zoldyck Family", value: "zoldyck-family" },
        { label: "Heavens Arena", value: "heavens-arena" },
        { label: "Yorknew City", value: "yorknew-city" },
        { label: "Greed Island", value: "greed-island" },
        { label: "Chemira Ant", value: "chemira-ant" },
        {
          label: "13th Hunter Chairman Election",
          value: "13th-hunter-chairman-election",
        },
      ],
      favoriteArc: "",
      favoriteCharacter: "",
      favoriteCharacters: [],
    };
  },
  methods: {
    handleKeyUp(event) {
      const { key, target } = event;
      const { value } = target;

      if (key !== ",") return;

      const character = value.slice(0, value.indexOf(","));
      if (character) {
        this.favoriteCharacters.push(character);
      }
      this.favoriteCharacter = "";
    },
    deleteCharacter(characterToDelete) {
      this.favoriteCharacters = this.favoriteCharacters.filter(
        (character) => character !== characterToDelete
      );
    },
  },
};
</script>

<style scoped></style>
