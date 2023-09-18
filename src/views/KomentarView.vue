<template>
 
  <v-container >
      <v-row justify="center">
        <v-col cols="12" md="8">
          <v-card elevation="2">
            <v-card-title class="headline">Podijelite s nama svoje mišljenje:</v-card-title>
            <v-card-text><br>
              <v-form @submit.prevent="submitForm">
                <v-text-field
                  v-model="username"
                  label="Korisničko ime"
                  outlined
                  required
                  :rules="nameRules"
                ></v-text-field>
                <div class="text-left mt-4">
                  <h2>Odaberite ocjenu:</h2>
                  <div class="rating">
                    <span
                      v-for="star in 5"
                      :key="star"
                      @click="setRating(star)"
                      :class="{ 'filled': star <= selectedRating }"
                    >
                      &#9733;
                    </span><br>
                  </div>
                </div><br>
                <v-textarea
                  v-model="comment"
                  label="Komentar"
                  outlined
                  rows="3"
                  clearable
                ></v-textarea>
                <v-file-input accept="image/*" label="Dodajte sliku"></v-file-input>
                <v-btn
                  color="primary"
                  class="mt-4"
                  type="submit"
                >
                  OSTAVI KOMENTAR!
                </v-btn>
              </v-form>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: "",
        selectedRating: 0,
        comment: "",
        nameRules: [
          v => !!v || "Korisničko ime je obavezno",
          v => (v && v.length >= 3) || "Korisničko ime mora biti najmanje 3 znaka"
        ],
      };
    },
    methods: {
      setRating(rating) {
        this.selectedRating = rating;
      },
      submitForm() {
        if (this.selectedRating > 0 && this.comment.trim() !== "") {
          // Ovdje možete dodati logiku za slanje ocjene i komentara na server
          console.log("Korisničko ime:", this.username);
          console.log("Ocjena:", this.selectedRating);
          console.log("Komentar:", this.comment);
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .rating {
    font-size: 24px;
    cursor: pointer;
  }
  .filled {
    color: gold;
  }
 .headline{
  font-style: oblique;
  text-align:right;
  font-style: italic;
 }


  </style>
  