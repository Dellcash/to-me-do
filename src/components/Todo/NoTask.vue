<template>
  <div class="no-tasks text-center">
    <v-icon size="100" color="primary">
      mdi-check
    </v-icon>
    <div class="div parand primary--text">یادداشتی نیست</div>
  </div>
</template>

<style lang="sass" scoped>
  .no-tasks
    position: absolute
    left: 50%
    top: 50%
    transform: translate(-50%, -50%)
    opacity: 0.5

.parand
  font-family: "Parand"

.div
  font-size: 2rem !important
</style>
