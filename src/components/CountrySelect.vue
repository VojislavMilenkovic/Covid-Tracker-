<template>
  <select @change="onChange" v-model="selected">
    <option value="0">Select Country</option>
    <option v-for="country in countries" :value="country.ID" :key="country.ID">
      {{ country.Country }}
    </option>
  </select>
</template>

<script>
export default {
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onChange() {
      const country = this.countries.find((item) => {
        return item.ID === this.selected;
      });

      this.$emit("get-country", country);
    },
  },
};
</script>

<style>
</style>