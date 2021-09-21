<template>
  <v-dialog :value="true" persistent max-width="290">
    <v-card>
      <v-card-title class="v-c-t parand">
        ویرایش
      </v-card-title>
      <v-card-text class="parand"
        >ویرایش عنوان این وظیفه:
        <v-text-field v-model="taskTitle" />
      </v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn class="parand" text @click="$emit('close')">
          لغو
        </v-btn>
        <v-btn class="parand" color="red darken-1" text @click="saveTask">
          ذخیره
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  props: ["task"],
  data() {
    return {
      taskTitle: null,
    };
  },
  methods: {
    saveTask() {
      let payload = {
        id: this.task.id,
        title: this.taskTitle,
      };
      this.$store.commit("updateTaskTitle", payload);
    },
  },
  mounted() {
    this.taskTitle = this.task.title;
  },
};
</script>

<style lang="sass" scoped>
.parand
  font-family: "Parand"
.v-c-t
  font-size: 1rem
</style>
