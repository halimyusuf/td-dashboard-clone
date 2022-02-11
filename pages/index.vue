<template>
  <div class="dashboard">
    <template>
      <dashboard-intro />
    </template>

    <div class="mt-10">
      <v-row>
        <v-col cols="12" lg="4" md="6" sm="6" v-for="c in cards" :key="c.label">
          <dashboard-card
            :label="c.label"
            :value="c.value"
            :percent-change="c.percentChange"
            :increase="c.increase"
          />
        </v-col>
      </v-row>
    </div>

    <div class="mt-10">
      <dashboard-table />
    </div>
  </div>
</template>

<script>
import DashboardCard from "../components/dashboard/Card.vue";
import DashboardIntro from "../components/dashboard/Intro.vue";
import DashboardTable from "../components/dashboard/table/index.vue";
import cardContent from "../data/cardContent";
export default {
  name: "IndexPage",
  components: {
    DashboardCard,
    DashboardTable,
    DashboardIntro,
  },
  data() {
    return {
      cards: cardContent.cards,
    };
  },
};
</script>

<style>
.dashboard {
  padding: 48px 0px 96px;
}

@media screen and (max-width: 600px) {
  .welcome-text div:nth-child(1) {
    font-size: 24px;
    line-height: 32px;
  }

  .dashboard {
    padding: 32px 0px 48px;
  }
}
</style>
