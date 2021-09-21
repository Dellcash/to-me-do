<template>
  <v-text-field
    @click:append="addTask"
    @keyup.enter="addTask"
    v-model="newTaskTitle"
    class="pa-4 parand"
    outlined
    label="مینویسی؟"
    append-icon="mdi-plus"
    hide-details
    clearable
  ></v-text-field>
</template>

<script>
export default {
  data() {
    return {
      newTaskTitle: "",
    };
  },
  methods: {
    addTask() {
      this.$store.dispatch("addTask", this.newTaskTitle);
      this.newTaskTitle = "";
    },
  },
};
</script>

<style lang="sass" scoped>
.parand
  font-family: "Parand"
</style>
