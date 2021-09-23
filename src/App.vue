<template>
  <v-app id="inspire">
    <v-navigation-drawer right app v-model="drawer" :mobile-breakpoint="768">
      <v-img
        class="pa-4 pt-7"
        height="170"
        src="mountains.jpg"
        gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
      >
        <v-avatar size="70" class="mb-1">
          <img src="profile.jpeg" alt="Dellcash" />
        </v-avatar>
        <div
          class="white--text parand pr-2 mt-2 "
          style="font-size:1rem; font-weight:bold !important"
        >
          امید دلکش
        </div>
        <div
          class="white--text text-subtitle-2 pr-2"
          style="font-family: 'Courier New', Courier, monospace !important"
        >
          dellcash@
        </div>
      </v-img>

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
      height="170"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        >
        </v-img>
      </template>

      <v-container class="header-container">
        <v-row>
          <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
          <v-spacer></v-spacer>
          <search />
        </v-row>
        <v-row>
          <v-toolbar-title class="mosa mr-3 pb-3" style="font-size:2.125rem">
            برام‌انجام‌میدی؟
          </v-toolbar-title>
        </v-row>
        <v-row class="mt-0">
          <live-date-time />
        </v-row>
      </v-container>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
      <snack-bar />
    </v-main>
  </v-app>
</template>

<script>
export default {
  components: {
    "snack-bar": require("@/components/Shared/Snackbar.vue").default,
    search: require("@/components/Tools/Search.vue").default,
    "live-date-time": require("@/components/Tools/LiveDateTime.vue").default,
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
.header-container
  max-width: none !important
  
.row + .row
    margin-top: 8px

.mosa
  font-family: "Mosa"

.parand
  font-family: 'Parand'

.v-list-item__content > *:not(:last-child)
  font-size: 2rem

.v-list-item__title
  font-family: "mosa"

.v-list--dense .v-list-item .v-list-item__title
  font-size: 1rem !important

.v-app-bar-title__content
  font-family: "Mosa"

@font-face
  font-family: "Parand"
  src: url("./fonts/Mj_Parand.TTF")

@font-face
  font-family: "Mosa"
  src: url("./fonts/Mj_Mousa.TTF")
</style>
