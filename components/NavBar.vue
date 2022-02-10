<template>
  <v-sheet>
    <div class="nav-1">
      <v-container class="pa-0">
        <v-app-bar color="#fff" elevation="0">
          <v-toolbar-title>
            <img src="../assets/Vector.svg" />
          </v-toolbar-title>
          <render-nav-links
            :nav-links="navLinks"
            :set-current-link="setCurrentLink"
            :current-link="currentLink"
          />
          <v-spacer />

          <div class="d-none d-sm-flex align-center ml-5">
            <!-- nav btn -->
            <div class="ml-3">
              <v-btn outlined class="cust-btn" color="#7F56D9">
                <v-icon color="#344054">mdi-lightning-bolt-outline</v-icon>
                <div class="ml-2 cust-btn-text">Upgrade now</div>
              </v-btn>
            </div>
            <!-- settings icon -->
            <div class="ml-3">
              <v-btn icon small>
                <v-icon>mdi-cog-outline</v-icon>
              </v-btn>
            </div>
            <!-- bell icon -->
            <div class="ml-3">
              <v-btn icon small>
                <v-icon>mdi-bell-outline</v-icon>
              </v-btn>
            </div>
            <!-- nav avatar -->
            <div class="ml-3">
              <v-avatar width="40" height="40">
                <img src="../assets/navAvatar.svg" />
              </v-avatar>
            </div>
          </div>

          <v-btn icon class="d-md-none">
            <v-icon>mdi-menu</v-icon>
          </v-btn>
        </v-app-bar>
      </v-container>
    </div>
    <nav-bar-2 />
  </v-sheet>
</template>

<script>
import RenderNavLinks from "./RenderNavLinks.vue";
export default {
  components: { RenderNavLinks },
  props: ["setRightDrawer"],
  data() {
    return {
      currentLink: null,
      navLinks: [
        { label: "Home", route: "/" },
        { label: "Dashboard", route: "/" },
        { label: "Projects", route: "/" },
        { label: "Tasks", route: "/" },
        { label: "Reporting", route: "/" },
        { label: "Users", route: "/" },
      ],
    };
  },
  methods: {
    setCurrentLink(link) {
      this.currentLink = link;
    },
  },
};
</script>

<style>
.nav-1 {
  border-bottom: 1px solid #eaecf0 !important;
}
</style>