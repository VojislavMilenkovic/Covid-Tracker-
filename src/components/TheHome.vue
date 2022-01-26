<template>
  <main v-if="!loading">
    <data-title :text="title" :dataDate="dataDate"></data-title>
    <data-boxes :statistics="statistics"></data-boxes>
    <div class="d-md-flex justify-content-md-around align-items-center">
      <country-select
        :countries="countries"
        @getCountry="getCountryData"
      ></country-select>
      <button
        v-if="statistics.Country"
        @click="showGlobalData"
        class="btn btn-primary rounded-pill py-3 px-5"
      >
        Show Global data
      </button>
    </div>
  </main>
  <main v-else class="hourglass">
    <div>Fetching Data...</div>
    <img :src="loadingImg" alt="" />
  </main>
</template>

<script>
import DataTitle from "./DataTitle.vue";
import DataBoxes from "./DataBoxes.vue";
import CountrySelect from "./CountrySelect.vue";
export default {
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect,
  },
  data() {
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      statistics: {},
      countries: [],
      loadingImg: require("../assets/hourglass.gif"),
    };
  },
  methods: {
    async fetchCovidData() {
      const response = await fetch("https://api.covid19api.com/summary");
      const data = await response.json();
      return data;
    },
    getCountryData(country) {
      this.statistics = country;
      this.title = country.Country;
    },
    async showGlobalData() {
      this.loading = true;
      const data = await this.fetchCovidData();
      this.title = "Global";
      this.statistics = data.Global;
      this.loading = false;
    },
  },
  async created() {
    const data = await this.fetchCovidData();
    this.dataDate = data.Date;
    this.statistics = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>

<style>
.hourglass {
  font-size: 40px;
}
</style>