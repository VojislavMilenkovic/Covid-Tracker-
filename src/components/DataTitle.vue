<template>
  <div class="data-title py-4">
    <h2>{{ text }}</h2>
    <div>
      {{ timestamp }}
    </div>
  </div>
</template>

<script>
import moment from "moment";
export default {
  props: ["text", "dataDate"],
  computed: {
    timestamp() {
      return moment(this.dataDate).format("Do MMM YYYY, h:mm:ss a");
    },
  },
};
</script>

<style scoped>
.data-title {
  font-size: 20px;
}
</style>