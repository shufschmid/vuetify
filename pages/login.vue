<template>
  <v-card width="400" class="mx-auto mt-5">
    <v-card-title>Login</v-card-title>
    <v-card-text>
      <v-form>
        <v-text-field
          v-model="username"
          name="username"
          label="Username"
          required
          prepend-icon="mdi-account-circle"
        >
        </v-text-field>
        <v-text-field
          v-model="password"
          name="password"
          label="Password"
          required
          prepend-icon="mdi-lock"
          :type="show ? 'text' : 'password'"
          :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
          @click:append="show = !show"
        >
        </v-text-field>
      </v-form>
    </v-card-text>
    <v-card-actions>
      <v-btn color="success">Login</v-btn>
      <v-spacer />
      <v-btn color="primary">Register</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      password: '',
      username: '',
    }
  },
}
</script>
