<template>
  <!-- <v-sheet elevation="2" :rounded="10" style="overflow: hidden"> -->
  <div>
    <div>
      <dashboard-table-filters :filters="filters" />
    </div>

    <v-sheet elevation="2" class="mt-10">
      <v-data-table
        v-model="selected"
        :headers="headers"
        :items="tableContent"
        :page.sync="page"
        :single-select="false"
        hide-default-footer
        show-select
        :items-per-page="itemsPerPage"
        mobile-breakpoint="0"
      >
        <template v-slot:header.data-table-select="props">
          <v-btn @click="setSelectedHeader" icon small>
            <custom-checkbox
              :data="props"
              :selected="selected"
              :header="true"
              :selected-all="selectedAll"
            ></custom-checkbox>
          </v-btn>
        </template>

        <template v-slot:item.data-table-select="props">
          <v-btn @click="() => setSelected(props.item)" icon small>
            <custom-checkbox
              :data="props"
              :selected="selected"
              :selected-all="selectedAll"
            ></custom-checkbox>
          </v-btn>
        </template>

        <template v-slot:item.company="{ item }">
          <div class="d-flex">
            <div class="mr-3">
              <img
                :src="require(`../assets/company logo/${item.company.logo}`)"
              />
            </div>
            <div class="company-label">
              <div>
                {{ item.company.name }}
              </div>
              <div>
                {{ item.company.url }}
              </div>
            </div>
          </div>
        </template>
        <template v-slot:item.status="props">
          <div>
            <v-chip
              :color="isCustomer(props.item.status) ? '#ECFDF3' : '#F2F4F7'"
              small
            >
              <div
                :style="`${
                  isCustomer(props.item.status) ? 'color: #027a48' : '#344054'
                }`"
              >
                {{ props.item.status }}
              </div>
            </v-chip>
          </div>
        </template>
        <template v-slot:item.about="{ item }">
          <div class="about-text">
            <div>{{ item.about.text1 }}</div>
            <div>{{ item.about.text2 }}</div>
          </div>
        </template>
        <template v-slot:item.users="{ item }">
          <div class="table-users">
            <div
              v-for="(user, i) in item.users.slice(0, 5)"
              :key="user.profile_url"
            >
              <div :style="`position: absolute; left: -${i * 6}px`">
                <img
                  :src="require(`../assets/table avatars/${user.profile_url}`)"
                />
              </div>
            </div>
            <div v-if="item.users.slice(5).length">
              <div class="profile-text-avatar">
                <div>
                  <span> +{{ item.users.slice(5).length }} </span>
                </div>
              </div>
            </div>
          </div>
        </template>
        <template v-slot:item.edit="props">
          <v-btn icon small>
            <v-icon>{{ "mdi-" + props.item.edit }}</v-icon>
          </v-btn>
        </template>
        <template v-slot:item.delete="props">
          <v-btn icon small>
            <v-icon>{{ "mdi-" + props.item.delete }}</v-icon>
          </v-btn>
        </template>
        <template v-slot:item.licenseUse="props">
          <div style="width: 88px">
            <v-progress-linear
              height="8px"
              color="#7F56D9"
              rounded
              :value="props.item.licenseUse * 10"
              background-color="#F9F5FF"
            ></v-progress-linear>
          </div>
          <div>
            <v-icon>{{ "mdi-" + props.item.licenseUse }}</v-icon>
          </div>
        </template>
      </v-data-table>

      <div class="d-none d-sm-block">
        <dashboard-table-footer />
      </div>
    </v-sheet>
    <div>
      <div class="d-sm-none mt-7" style="border-top: 1px solid #eaecf0">
        <dashboard-table-footer />
      </div>
    </div>
  </div>
  <!-- </v-sheet> -->
</template>
 

<script>
import tableData from "../data/tableContent";
import CustomCheckbox from "./CustomCheckbox.vue";
import CustomSearchTextField from "./CustomSearchTextField.vue";
import DashboardTableFilters from "./DashboardTableFilters.vue";
import DashboardTableFooter from "./DashboardTableFooter.vue";
export default {
  components: {
    CustomCheckbox,
    CustomSearchTextField,
    DashboardTableFilters,
    DashboardTableFooter,
  },
  data() {
    return {
      // https://robohash.org/wwwww
      singleSelect: false,
      page: 1,
      itemsPerPage: 7,
      filters: [
        {
          filter: "All time",
        },
        { filter: "US,AU,+4" },
      ],
      selected: [],
      selectedAll: false,
      headers: tableData.headers,
      tableContent: tableData.content,
    };
  },
  methods: {
    isCustomer(status) {
      return status.toLowerCase() === "customer";
    },
    setSelectedHeader() {
      if (this.selectedAll) {
        this.selected = [];
      } else {
        const ss = this.tableContent.map((a) => a.company.name);
        for (let a of ss) {
          this.selected.push(a);
        }
      }
      this.selectedAll = !this.selectedAll;
      console.log(this.selected);
    },
    setSelected(item) {
      const value = this.selected.find((a) => a === item.company.name);
      console.log(this.selected);
      if (!value) {
        this.selected.push(item.company.name);
      } else {
        this.selected = this.selected.filter((a) => a !== item.company.name);
      }
    },
  },
};
</script>

<style>
.table-users {
  display: flex;
  align-items: center;
}

.table-users div {
  position: relative;
  width: 24px;
  height: 24px;
}

.profile-text-avatar {
  position: absolute;
  left: -30px;
}

.profile-text-avatar div {
  background-color: #f9f5ff;
  width: 26px;
  height: 26px;
  border: 3px solid #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
}

.pagination-page {
  color: #344054;
}

.profile-text-avatar span {
  color: #7f56d9;
  font-size: 12px;
  font-weight: 500;
}
/* .table-users div div.mark-left {
  position: absolute;
  left: 10px;
} */

table tbody tr:nth-child(odd) {
  background: #f9fafb;
}

table tbody tr td {
  border: none !important;
  height: 72px !important;
}
.about-text div {
  white-space: nowrap;
}
.about-text div:nth-child(1) {
  line-height: 20px;
  color: #101828;
}

.about-text div:nth-child(2) {
  line-height: 20px;
  color: #667085;
}

.company-label div:nth-child(1) {
  color: #101828;
  font-weight: 500;
  line-height: 20px;
}
.company-label div:nth-child(2) {
  color: #667085;
  line-height: 20px;
}
</style>