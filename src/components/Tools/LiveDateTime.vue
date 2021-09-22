<template>
  <div class="parand mr-3" style="font-size: 1.10rem">
    <!-- ۱ مهر , ۱۵:۲۸ -->
    {{ date }}
  </div>
</template>

<script>
import { format } from "date-fns-jalali";

export default {
  data() {
    return {
      date: "",
    };
  },
  methods: {
    getDate() {
      this.date = format(new Date(), "d MMMM، H:mm:ss");
      setTimeout(this.getDate, 1000)
    },
  },
  mounted() {
    this.getDate();
  },
};
</script>

<style lang="sass" scoped>
.parand
  font-family: 'parand'
</style>
