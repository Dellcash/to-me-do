<template>
  <div class="home ">
    <field-add-task />

    <list-tasks v-if="$store.state.tasks.length" />

    <no-tasks v-else />

    <button-done-sorting v-if="$store.state.sorting" />
  </div>
</template>

<script>
export default {
  components:{
    'button-done-sorting': require('@/components/Todo/ButtonDoneSorting.vue').default,
    'field-add-task': require('@/components/Todo/FieldAddTask.vue').default,
    'list-tasks': require('@/components/Todo/ListTasks.vue').default,
    'no-tasks': require('@/components/Todo/NoTask.vue').default

  },
  name: "Home",
};
</script>
