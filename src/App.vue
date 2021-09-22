<template>
  <v-app id="inspire">
    <v-navigation-drawer right app v-model="drawer">
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="mosa">
            برام‌انجام‌میدی؟
          </v-list-item-title>
          <v-list-item-subtitle>
            Best Todo Ever
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense nav>
        <v-list-item v-for="item in items" :key="item.title" link :to="item.to">
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      color="teal lighten-3"
      dark
      prominent
      src="mountains.jpg"
    >
        <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title class="mosa">انجام بده ‌...</v-app-bar-title>

      <v-spacer></v-spacer>
        <search />
    </v-app-bar>

    <v-main>
      <router-view></router-view>
      <snack-bar />
    </v-main>
  </v-app>
</template>

<script>
export default {
  components:{
    'snack-bar': require('@/components/Shared/Snackbar.vue').default,
    'search': require('@/components/Tools/Search.vue').default
  },
  data: () => ({
    drawer: null,
    items: [
      { title: "وظایف", icon: "mdi-format-list-checks", to: "/" },
      { title: "درباره", icon: "mdi-help-box", to: "/about" },
    ],
  }),
};
</script>

<style lang="sass" scoped>
.mosa
  font-family: "Mosa"

.v-list-item__content > *:not(:last-child)
  font-size: 2rem

.v-list-item__title
  font-family: "mosa"

.v-list--dense .v-list-item .v-list-item__title
  font-size: 1rem !important

.v-list-item__subtitle
  font-family: "Courier New", Courier, monospace
  font-weight: bold
  direction: ltr

.v-app-bar-title__content
  font-family: "Mosa"

@font-face
  font-family: "Parand"
  src: url("./fonts/Mj_Parand.TTF")

@font-face
  font-family: "Mosa"
  src: url("./fonts/Mj_Mousa.TTF")
</style>

