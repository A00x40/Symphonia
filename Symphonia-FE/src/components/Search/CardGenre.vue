<template>
  <v-card
    class="mx-auto"
    cols="4"
    height="12.5rem"
    :href="/genre/ + ID"
    color="#b3b3b3"
    elevation="4"
    :id="ID"
  >
    <v-card-title>{{ name }}</v-card-title>
  </v-card>
</template>

<script>
export default {
  /**
   * This page is used to view the cards in search view
   * @displayName Search Cards
   * @example [none]
   */
  props: {
    name: String,
    ID: String
  }
};
</script>

<style scoped>
a {
  margin-bottom: 2.5rem;
}
</style>
