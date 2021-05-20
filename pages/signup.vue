<template>
  <div>
    <v-row>
      <v-col>
        <h1>Signup</h1>
        <v-form ref="form" v-model="formValidity">
          <v-text-field label="E-Mail" type="email" :rules="emailRules" />
          <v-autocomplete label="Which browser do you use?" :items="browsers" />
          <v-file-input label="Upload your Profile-Picture" />
          <v-menu
            ref="menu"
            v-model="menu"
            :close-on-content-click="false"
            :return-value.sync="date"
            transition="scale-transition"
            offset-y
            min-width="auto"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-text-field
                v-model="date"
                label="Picker in menu"
                prepend-icon="mdi-calendar"
                readonly
                v-bind="attrs"
                v-on="on"
              ></v-text-field>
            </template>
            <v-date-picker
              v-model="date"
              no-title
              scrollable
              :first-day-of-week="1"
              locale="de-CH"
            >
              <v-spacer></v-spacer>
              <v-btn text color="primary" @click="menu = false"> Cancel </v-btn>
              <v-btn text color="primary" @click="$refs.menu.save(date)">
                OK
              </v-btn>
            </v-date-picker>
          </v-menu>
          <v-checkbox label="I accept Terms & Conditions?" />
          <v-btn type="submit" :disabled="!formValidity" @click="validateForm"
            >Submit</v-btn
          >
        </v-form>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formValidity: false,
      emailRules: [(value) => !!value || 'emailadress not correct'],
      browsers: [
        'Internet Explorer',
        'Chrome',
        'Safari',
        'Firefox',
        'Edge',
        'other',
      ],
      date: new Date().toISOString().substr(0, 10),
      menu: false,
    }
  },
  methods: {
    validateForm() {
      this.$ref.form.validate()
    },
  },
}
</script>

<style scoped></style>
