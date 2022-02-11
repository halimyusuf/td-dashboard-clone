<template>
  <v-app>
    <nav-bar />
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <!-- <nav-drawer /> -->
  </v-app>
</template>

<script>
import NavBar from "../components/navbar/NavBar.vue";
export default {
  components: { NavBar },
  name: "DefaultLayout",
  methods: {},
};
</script>

<style>
body {
  max-width: 100vw;
  overflow: hidden;
}

.cust-btn {
  border: 1px solid #d0d5dd !important;
  border-radius: 8px;
}

.cust-pry-btn {
  border-radius: 8px;
}

.cust-pry-btn-text {
  font-size: 14px;
  font-weight: 500;
  line-height: 20px;
  letter-spacing: 0em;
  text-transform: capitalize;
  color: #6941c6 !important;
}

.cust-btn-text {
  font-size: 14px;
  font-weight: 500;
  line-height: 20px;
  letter-spacing: 0em;
  text-align: left;
  text-transform: capitalize;
  color: #344054 !important;
}

.cust-btn-text-dark {
  color: #fff !important;
}
</style>
