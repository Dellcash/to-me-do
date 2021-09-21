<template>
  <v-dialog :value="true" persistent max-width="290">
    <v-card>
      <v-card-title class="v-c-t parand">
        می‌خوایی پاکش کنی؟
      </v-card-title>
      <v-card-text class="parand"
        >مطمئنی می‌خوایی این وظیفه رو پاک کنی؟</v-card-text
      >
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn class="parand" text @click="$emit('close')">
          نه
        </v-btn>
        <v-btn
          class="parand"
          color="red darken-1"
          text
          @click="$store.dispatch('deleteTask', task.id)"
        >
          اره
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  props: ["task"],
};
</script>

<style lang="sass" scoped>
.parand
  font-family: "Parand"
.v-c-t
  font-size: 1rem
  
</style>
