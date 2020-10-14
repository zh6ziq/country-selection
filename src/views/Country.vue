<template>
  <div>
    <h1>This is country page.</h1>
    <b-dropdown id="dropdown-1" text="Dropdown Button" class="m-md-2">
      <b-dropdown-item v-for="country in countries" :key="country.alpha3code">{{
        country.name
      }}</b-dropdown-item>
    </b-dropdown>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      countries: []
    };
  },

  created() {
    this.loadAllCountries();
  },

  methods: {
    loadAllCountries() {
      axios
        .get("https://restcountries.eu/rest/v2/all")
        .then(respond => {
          this.countries = respond.data;
        })
        .catch(err => {
          console.log(err);
        });
    }
  }
};
</script>

<style scoped></style>
