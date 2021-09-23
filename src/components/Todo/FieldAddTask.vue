<template>
  <v-text-field
    @keyup.enter="addTask"
    v-model="newTaskTitle"
    class="pa-4 field-add-task"
    outlined
    placeholder="چیکار می‌خوایی کنی؟"
    hide-details
    clearable
  >
    <template v-slot:append>
      <v-icon @click="addTask" :disabled="newTaskTitleInvalid"
        >mdi-plus</v-icon
      >
    </template>
  </v-text-field>
</template>

<script>
export default {
  data() {
    return {
      newTaskTitle: "",
    };
  },
  computed: {
    newTaskTitleInvalid() {
      return !this.newTaskTitle;
    },
  },
  methods: {
    addTask() {
      if (!this.newTaskTitleInvalid) {
        this.$store.dispatch("addTask", this.newTaskTitle);
        this.newTaskTitle = "";
      }
    },
  },
};
</script>

<style lang="sass" scoped>
  .field-add-task
    font-family: 'Parand'
    .v-input--is-focused
      .v-input__slot
        background: rgba(31,94,129, 0.5) !important
</style>
