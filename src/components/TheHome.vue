<template>
  <main v-if="!loading">
    <data-title :text="title" :dataDate="dataDate"></data-title>
    <data-boxes :statistics="statistics"></data-boxes>
    <country-select
      :countries="countries"
      @getCountry="getCountryData"
    ></country-select>
    <button v-if="statistics.Country" @click="showGlobalData">
      Show Global data
    </button>
  </main>
  <main v-else>
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
</style>