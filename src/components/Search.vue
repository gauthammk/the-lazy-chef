<template>
  <v-container class="col-lg-6 col-xs-8">
    <v-toolbar>
      <v-text-field
        color="green"
        style="width: 100%;"
        hide-details
        single-line
        clearable
        placeholder="What's in your kitchen?"
        v-model="ingredients"
        type="text"
      />
      <v-spacer></v-spacer>
      <v-btn icon v-on:click="getRecipes" color="green">
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