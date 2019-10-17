<template>
  <v-dialog
      v-model="dialog"
      max-width="500"
    >
    <template v-slot:activator="{ on }">
      <v-btn
        text
        class="success"
        v-on="on"
      >
        Add new project
      </v-btn>
    </template>

    <v-card>
        <v-card-title
        >
          Add a new project
        </v-card-title>

        <v-card-text>
          <v-form class="px-3" ref="form">
            <v-text-field
              label="Title"
              v-model="title"
              :rules="inputRules"></v-text-field>
            <v-textarea
              :rules="inputRules"
              label="Information"
              v-model="content"></v-textarea>
            <v-menu max-width="290">
              <template v-slot:activator="{ on }">
                <v-text-field
                  :rules="inputRules"
                  :value="dueDate"
                  v-on="on"
                  label="Due date">
                </v-text-field>
              </template>
              <v-date-picker
                v-model="dueDate"
                @change="menu1 = false"
              ></v-date-picker>
            </v-menu>
          </v-form>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            class="success"
            text
            @click="submit"
          >
            Add project
          </v-btn>
        </v-card-actions>
      </v-card>
  </v-dialog>
</template>

<script>
import format from 'date-fns/format'
export default {
  data() {
    return {
      title: '',
      content: '',
      dueDate: null,
      inputRules: [
        v => v.length >= 3 || 'Minimun length is 3 characters'
      ]
    }
  },
  methods: {
    submit() {
      if(this.$refs.form.validate()) {
        console.log(this.title, this.content)
      }
    }
  }
}
</script>

<style>

</style>