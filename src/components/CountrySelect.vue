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

<style scoped>
select {
  border: 1px solid blue;
  border-radius: 5px;
  padding: 5px 3px;
  margin-bottom: 15px;
}
option {
  font-size: 15px;
}
</style>