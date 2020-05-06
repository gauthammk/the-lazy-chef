<template>
  <v-container>
    <div v-if="recipes.length > 0">
      <h3 class="text-center">Recipes</h3>
      <div v-bind:key="recipe.id" v-for="recipe in recipes">
        <v-container class="col-xs-8 col-lg-6" xs="8">
          <v-card>
            <v-card-title>{{ recipe.title }}</v-card-title>
            <v-card-text>
              <v-chip-group>
                <v-chip
                  v-for="ingredient in recipe.ingredients.split(',')"
                  :key="ingredient"
                >{{ ingredient }}</v-chip>
              </v-chip-group>
              <v-btn class="mx-2" fab dark small color="green" :href="recipe.href">
                <v-icon>mdi-open-in-new</v-icon>
              </v-btn>
            </v-card-text>
          </v-card>
        </v-container>
      </div>
    </div>
    <div v-else dark>
      <v-container class="col-6 text-center green--text">
        <h4 color="green">Please try a new search term.</h4>
      </v-container>
    </div>
  </v-container>
</template>

<script>
export default {
  name: "Recipes",
  props: ["recipes"]
};
</script>

<style>
</style>