<template>
  <nav>
    <v-toolbar text app>
      <v-toolbar-side-icon class="grey--text" @click="drawer=!drawer">
        <v-icon>mdi-menu</v-icon>
      </v-toolbar-side-icon>
      <v-toolbar-title>
        <span class="font-weight-light">Vuetify</span>
        <span>Projects</span>
      </v-toolbar-title>
      <v-spacer/>

      <v-menu offset-y>
        <template v-slot:activator="{ on }">
          <v-btn text v-on="on" color="grey">
            <v-icon left>mdi-chevron-down</v-icon>
            <span>Menu</span>
          </v-btn>
        </template>
        <v-list>
          <v-list-item v-for="link in links" :key="link.text" router :to="link.route">
            <v-list-item-title>{{ link.text }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>

      <v-btn text color="grey">
        <span>Sign Out</span>
        <v-icon right>mdi-logout</v-icon>
      </v-btn>
    </v-toolbar>

    <v-navigation-drawer v-model="drawer" app class="primary">
      <v-layout column align-center>
        <v-flex class="mt-5">
          <v-avatar size="100">
            <img src="/avatar-5.png" alt="">
          </v-avatar>
          <p class="white--text subheading mt-3">
            Max Efi
          </p>
        </v-flex>
        <v-flex class="mt-4 mb-3">
          <Popup />
        </v-flex>
      </v-layout>
      <v-list>
        <v-list-item class="white--text" v-for="link in links" :key="link.text" router :to="link.route">
          <v-list-item-action>
            <v-icon class="white--text">{{ link.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="white--text">
              {{ link.text }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

  </nav>
</template>

<script>
import Popup from './Popup'

export default {
  components: {
    Popup
  },
  data() {
    return {
      drawer: false,
      links: [
        {icon: 'mdi-view-dashboard', text: 'Dashboard', route: '/'},
        {icon: 'mdi-folder', text: 'My Projects', route: '/projects'},
        {icon: 'mdi-account', text: 'Team', route: '/team'}
      ]
    }
  }
}
</script>

<style>

</style>