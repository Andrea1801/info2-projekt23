<template>
  <v-container>
    <h2>{{ cocktail.name }} Anketa</h2>
    <v-form>
      <v-radio-group v-model="selectedOption">
        <v-radio :label="option" :value="option" v-for="(option, index) in options" :key="index"></v-radio>
      </v-radio-group>
    </v-form>
    <v-btn color="primary" @click="submitSurvey">Pošalji odgovor</v-btn>
  </v-container>
</template>

<script>
export default {
  props: {
    cocktail: Object, // Primjer: { name: "Martini", options: ["Odličan", "Dobar", "Loš"] }
  },
  data() {
    return {
      selectedOption: null,
    };
  },
  computed: {
    options() {
      return this.cocktail.options;
    },
  },
  methods: {
    submitSurvey() {
      if (this.selectedOption) {
        // Ovdje možete dodatno obraditi odgovor, na primjer, poslati ga na server
        console.log(`Vaš odgovor za ${this.cocktail.name}: ${this.selectedOption}`);
      }
    },
  },
};
</script>
