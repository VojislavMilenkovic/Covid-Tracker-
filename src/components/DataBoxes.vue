<template>
  <div>
    <!-- Cases box starts-->
    <div>
      <h3>Cases</h3>
      <div>
        <span>New: </span>
        {{ numberWithCommas(statistics.NewConfirmed) }}
      </div>
      <div>
        <span>Total: </span>
        {{ numberWithCommas(statistics.TotalConfirmed) }}
      </div>
    </div>
    <!--Cases box ends-->
    <!-- Deaths box starts-->
    <div>
      <h3>Deaths</h3>
      <div>
        <span>New: </span>
        {{ numberWithCommas(statistics.NewDeaths) }}
      </div>
      <div>
        <span>Total: </span>
        {{ numberWithCommas(statistics.TotalDeaths) }}
      </div>
    </div>
    <!--Deaths box ends-->
  </div>
</template>

<script>
export default {
  props: ["statistics"],
  methods: {
    numberWithCommas(x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>

<style>
</style>