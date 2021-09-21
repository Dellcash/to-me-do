<template>
  <v-snackbar class="mosa" v-model="$store.state.snackbar.show">
    {{ $store.state.snackbar.text }}

    <template v-slot:action="{ attrs }">
      <v-btn
        text
        v-bind="attrs"
        @click="snackbar = $store.commit('hideSnackbar')"
      >
        بستن
      </v-btn>
    </template>
  </v-snackbar>
</template>

<style lang="sass" scoped>
.mosa
  font-family: 'Mosa'
</style>
