<template>
  <v-container class="col-6">
    <v-toolbar>
      <v-btn icon class="hidden-xs-only">
        <v-icon>mdi-delete</v-icon>
      </v-btn>

      <v-text-field
        style="width: 100%;"
        hide-details
        single-line
        placeholder="What's in your kitchen?"
        v-model="ingredients"
      />

      <v-spacer></v-spacer>

      <v-btn icon class="hidden-xs-only" v-on:click="getRecipes">
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-toolbar>
  </v-container>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      ingredients: ""
    };
  },
  methods: {
    getRecipes() {
      this.$emit("get-recipes", this.ingredients);
    }
  }
};
</script>

<style>
</style>