<template>
  <v-app class="app-container">
    <v-app-bar id="app-bar" style="" app color="primary" flat>
      <router-link class="toolbar-title-container" to="/dashboard">
        <v-toolbar-title style="font-size: 1.75em"> vumblr </v-toolbar-title>
      </router-link>
      <v-spacer></v-spacer>
      <v-btn
        class="nav-button github-button"
        href="https://github.com/neillsom/vumblr"
        target="_blank"
        depressed
        small
        height="32px"
        title="github.com/neillsom/vumblr"
        aria-label="github.com/neillsom/vumblr"
      >
        <v-icon color="#ffffff">mdi-github</v-icon>
      </v-btn>

      <v-btn
        class="nav-button"
        v-for="link in links"
        :key="`${link.label}-link`"
        :to="link.url"
        depressed
        small
        height="32px"
        :title="link.label"
        :aria-label="link.label"
      >
        <v-icon color="#ffffff">{{ link.icon }}</v-icon>
      </v-btn>
    </v-app-bar>
    <div class="theme-toggle">
      <v-btn
        @click="toggleTheme"
        fab
        small
        depressed
        color="primary"
        fixed
        right
        bottom
      >
        <v-icon> mdi-theme-light-dark</v-icon>
      </v-btn>
    </div>

    <v-main class="main-body">
      <div class="router-body">
        <router-view></router-view>
      </div>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data() {
    return {
      links: [
        {
          label: "Dashboard",
          url: "/dashboard",
          icon: "mdi-home",
        },

        // {
        //   label: "Signup",
        //   url: "/signup",
        //   icon: "mdi-account-plus",
        // },
        {
          label: "Account",
          url: "/account",
          icon: "mdi-account",
        },
        {
          label: "Inbox",
          url: "/inbox",
          icon: "mdi-email-outline",
        },

        {
          label: "New Post",
          url: "/new",
          icon: "mdi-pencil",
        },
      ],
    };
  },
  methods: {
    toggleTheme() {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
    },
  },
};
</script>

<style scoped>
/* w/o !important rule, vuetify overwrites style. chose this over inline styling */
.app-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: var(--v-background-base) !important;
}

.v-toolbar.v-app-bar#app-bar {
  font-weight: 900;
  font-family: "Helvetica Neue", HelveticaNeue, Helvetica, Arial, sans-serif;
  border-bottom: 1px solid rgba(255, 255, 255, 0.12) !important;
  display: flex;
  flex-direction: column;
  height: 54px !important;
}

.nav-button {
  margin: 0 10px;
}

.toolbar-title-container {
  color: #ffffff;
  text-decoration: none;
}

/* .main-body {
  width: 990px;
} */

.v-btn.nav-button {
  background: transparent !important;
}

.v-btn.nav-button:last-of-type {
  background: var(--v-secondary-base) !important;
}
</style>
