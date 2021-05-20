<template>
  <v-app>
    <v-app-bar color="blue" dense flat app dark>
      <v-app-bar-title>Vuetify-Tutorial</v-app-bar-title>
      <v-spacer />
      <v-btn v-for="link in links" :key="link.url" :to="link.url" nuxt>
        {{ link.name }}
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <footercomponent :nav-items="links"></footercomponent>
  </v-app>
</template>

<script>
import footercomponent from '@/components/footer.vue'

export default {
  components: { footercomponent },
  data() {
    return {
      username: '',
      password: '',
      links: [
        {
          url: '/',
          name: 'Home',
        },
        {
          url: '/login',
          name: 'Login',
        },
        {
          url: '/dashboard',
          name: 'Dashboard',
        },
        {
          url: '/signup',
          name: 'Signup',
        },
      ],
    }
  },
}
</script>
