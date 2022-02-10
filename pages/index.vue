<template>
  <div class="dashboard">
    <div class="d-flex justify-space-between flex-wrap">
      <div class="welcome-text mb-5">
        <div>Welcome back, Olivia</div>
        <div>Track, manage and forecast your customers and orders.</div>
      </div>
      <div>
        <v-btn outlined class="cust-btn" color="#7F56D9">
          <v-icon color="#344054">mdi-cloud-upload-outline</v-icon>
          <div class="ml-2 cust-btn-text">Upload</div>
        </v-btn>

        <v-btn class="cust-btn ml-2" color="#7F56D9" depressed dark>
          <v-icon color="#fff">mdi-plus</v-icon>
          <div class="ml-2 cust-btn-text cust-btn-text-dark">Add</div>
        </v-btn>
      </div>
    </div>

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
import DashboardCard from "../components/DashboardCard.vue";
import DashboardTable from "../components/DashboardTable.vue";
export default {
  name: "IndexPage",
  components: {
    DashboardCard,
    DashboardTable,
  },
  data() {
    return {
      cards: [
        {
          label: "Total customers",
          value: 2420,
          percentChange: 40,
          increase: true,
        },
        {
          label: "Members",
          value: 1210,
          percentChange: 10,
          increase: false,
        },
        {
          label: "Active now",
          value: 316,
          percentChange: 20,
          increase: true,
        },
      ],
    };
  },
};
</script>

<style>
.dashboard {
  padding: 48px 0px 96px;
}

.welcome-text div:nth-child(1) {
  font-size: 30px;
  font-weight: 500;
  line-height: 38px;
  letter-spacing: 0em;
  text-align: left;
  color: #101828;
  margin-right: 20px;
}

.welcome-text div:nth-child(2) {
  font-size: 16px;
  font-weight: 400;
  line-height: 24px;
  letter-spacing: 0em;
  text-align: left;
  color: #667085;
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

/* .table-ctrls {
  display: flex;

} */
</style>
