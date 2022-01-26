<template>
  <div class="row justify-content-around py-5 align-items-center">
    <!-- Cases box starts-->
    <div class="cases-box col-12 mb-2 col-md-5 mb-md-0 py-4 rounded-pill">
      <h3 class="box-title">Cases</h3>
      <div>
        <span class="box-new">New: </span>
        <span class="box-numbers">
          {{ numberWithCommas(statistics.NewConfirmed) }}
        </span>
      </div>
      <div>
        <span class="box-total">Total: </span>
        <span class="box-numbers">
          {{ numberWithCommas(statistics.TotalConfirmed) }}
        </span>
      </div>
    </div>
    <!--Cases box ends-->
    <!-- Deaths box starts-->
    <div class="death-box col-12 mb-2 col-md-5 mb-md-0 py-4 rounded-pill">
      <h3 class="box-title">Deaths</h3>
      <div>
        <span class="box-new">New: </span>
        <span class="box-numbers">
          {{ numberWithCommas(statistics.NewDeaths) }}
        </span>
      </div>
      <div>
        <span class="box-total">Total: </span>
        <span class="box-numbers">
          {{ numberWithCommas(statistics.TotalDeaths) }}
        </span>
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

<style scoped>
.cases-box {
  background-color: #89cff0;
}
.death-box {
  background-color: #6cb4ee;
}

.box-title {
  font-size: 30px;
}
.box-new,
.box-total {
  font-size: 20px;
}
.box-numbers {
  font-size: 30px;
  font-weight: 500;
}
</style>