<template>
  <div class="nav-2 d-none d-sm-block">
    <v-container class="pa-0">
      <v-app-bar color="#fff" elevation="0">
        <render-nav-links
          :nav-links="navLinks"
          :set-current-link="setCurrentLink"
          :current-link="currentLink"
          :first-link="true"
        />
        <v-spacer />
        <div class="search-cont ml-5">
          <custom-search-text-field placeholder="Searchhh" />
        </div>
      </v-app-bar>
    </v-container>
  </div>
</template>

<script>
export default {
  props: ["setRightDrawer"],
  data() {
    return {
      currentLink: null,
      upgradeBtnActive: false,
      navLinks: [
        { label: "Overview", route: "/" },
        { label: "Notification", route: "/" },
        { label: "Analysis", route: "/" },
        { label: "Saved reports", route: "/" },
        { label: "Trade History", route: "/" },
        { label: "User Reports", route: "/" },
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
.nav-2 {
  border-bottom: 1px solid #eaecf0 !important;
}

.search-cont {
  width: 320px;
  max-width: 100%;
}

.nav-btn {
  display: flex;
  align-items: center;
  border-radius: 8px;
  border: 1px solid #d0d5dd;
  box-shadow: 0px 1px 2px rgba(16, 24, 40, 0.05);
  padding: 6px 10px;
  cursor: pointer;

  /* font-size: 14px; */
}

.nav-btn.active {
  background: #7f56d9;
  color: #fff;
}
</style>