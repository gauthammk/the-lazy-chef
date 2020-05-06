<template>
  <v-app>
    <v-container fluid class="pa-0">
      <v-row>
        <v-col class="green white--text text-center">
          <h1 class="main-heading">The Lazy Chef</h1>
          <v-img src="./assets/tlc.png" width="15rem" class="mx-auto"></v-img>
          <Search v-on:get-recipes="getRecipes" />
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <Recipes v-bind:recipes="recipes" />
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
import Search from "./components/Search";
import Recipes from "./components/Recipes";
import fetch from "node-fetch";

export default {
  name: "App",
  components: {
    Search,
    Recipes
  },
  data: () => ({
    recipes: []
  }),
  methods: {
    getRecipes(ingredients) {
      //API call here.
      const url =
        "https://cors-anywhere.herokuapp.com/http://www.recipepuppy.com/api/?i=" +
        ingredients;
      console.log(ingredients, url);
      const getData = async url => {
        try {
          const response = await fetch(url);
          const json = await response.json();
          console.log(json);
          this.recipes = json.results;
          console.log(this.recipes);
        } catch (error) {
          console.log(error);
        }
      };
      getData(url);
    }
  }
};
</script>

<style scoped>
.main-heading {
  font-family: Lobster;
  font-size: 5rem;
}
</style>