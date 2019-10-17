<template>
  <div class="team">
    <h1 class="subheading grey--text">team</h1>

    <v-container class="my-5">
      <v-layout row>
        <v-flex xs12 sm6 md4 lg3
          v-for="person in team"
          :key="person.name">
          <v-card flat class="text-center ma-3">
            <v-responsive class="pt-4">
              <v-avatar size="100" class="grey lighten-2">
                <img :src="person.avatar" alt="">
              </v-avatar>
            </v-responsive>
            <v-card-text>
              <div class="subheading">{{ person.name }}</div>
              <div class="grey--text">{{ person.role }}</div>
            </v-card-text>
            <v-card-actions>
              <v-btn text color="grey">
                <v-icon small left>mdi-message</v-icon>
                <span>Message</span>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>

  </div>
</template>

<script>

export default {
  data() {
    return {
      team: [
        {name: 'Max Efi', role: 'Web developer', avatar: '/avatar-5.png'},
        {name: 'John Doe', role: 'Backend developer', avatar: '/avatar-2.png'},
        {name: 'Will Smith', role: 'Designer', avatar: '/avatar-3.png'},
        {name: 'Adam Yates', role: 'Sales manager', avatar: '/avatar-4.png'},
      ]
    }
  }
};
</script>