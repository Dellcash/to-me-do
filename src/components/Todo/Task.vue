<template>
  <div>
    <v-list-item
      @click="$store.dispatch('doneTask', task.id)"
      :class="{ 'blue lighten-5': task.done }"
      class="white"
      :ripple="false"
    >
      <template v-slot:default>
        <v-list-item-action>
          <v-checkbox :input-value="task.done" color="primary"></v-checkbox>
        </v-list-item-action>

        <v-list-item-content>
          <v-list-item-title
            class="parand"
            :class="{ 'text-decoration-line-through': task.done }"
            >{{ task.title }}</v-list-item-title
          >
        </v-list-item-content>

        <v-list-item-action v-if="task.dueDate">
          <v-list-item-action-text style="font-size:1rem" class="parand">
            <v-icon small>mdi-calendar</v-icon>
            {{ task.dueDate | newDate }}
          </v-list-item-action-text>
        </v-list-item-action>

        <v-list-item-action>
          <task-menu :task="task" />
        </v-list-item-action>

        <v-list-item-action v-if="$store.state.sorting">
          <v-btn class="handle" color="primary" icon >
            <v-icon>mdi-drag-horizontal-variant</v-icon>
          </v-btn>
        </v-list-item-action>
      </template>
    </v-list-item>
    <v-divider></v-divider>
  </div>
</template>

<script>
import { format } from "date-fns-jalali";

export default {
  props: ["task"],
  filters: {
    newDate(value) {
      return format(new Date(value), "d MMMM");
    },
  },
  components: {
    "task-menu": require("@/components/Todo/TaskMenu.vue").default,
  },
};
</script>

<style lang="sass" scoped>
.parand
  font-family: "Parand"

.v-list-item__title
  font-size: 1.2rem

.mosa
  font-family: "Mosa"

.sortable-ghost
  opacity: 0

.sortable-drag
  box-shadow: 0 0 10px rgba(0,0,0,.3)
</style>
