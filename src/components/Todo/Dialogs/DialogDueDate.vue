<template>
  <v-dialog
    ref="dialog"
    :value="true"
    :return-value.sync="date"
    persistent
    width="290px"
  >
    >
    <v-date-picker class="parand" v-model="date" scrollable locale="fa-ir">
      <v-spacer></v-spacer>
      <v-btn text color="primary" @click="$emit('close')">
        لغو
      </v-btn>
      <v-btn text color="success" @click="saveTask" :disabled="dateInvalid">
        ذخیره
      </v-btn>
    </v-date-picker>
  </v-dialog>
</template>

<script>
export default {
  props: ["task"],
  data() {
    return {
      date: null,
    };
  },
  computed:{
    dateInvalid(){
      return !this.date || this.date === this.task.dueDate
    }
  },
  methods: {
    saveTask() {
      let payload = {
        id: this.task.id,
        dueDate: this.date,
      };
      this.$store.dispatch("updateTaskDueDate", payload);
      this.$emit("close");
    },
  },
  mounted() {
    if (this.task.dueDate) {
      this.date = this.task.dueDate;
    }
  },
};
</script>

<style lang="sass" scoped>
.parand
  font-family: 'Parand'
</style>
