<template>
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
          <v-btn @click="setSelectedHeader" icon small color="#F9F5FF">
            <custom-checkbox
              :data="props"
              :selected="selected"
              :header="true"
              :selected-all="selectedAll"
            ></custom-checkbox>
          </v-btn>
        </template>

        <template v-slot:item.data-table-select="props">
          <v-btn
            @click="() => setSelected(props.item)"
            icon
            small
            color="#F9F5FF"
          >
            <custom-checkbox
              :data="props"
              :selected="selected"
              :selected-all="selectedAll"
            ></custom-checkbox>
          </v-btn>
        </template>

        <template v-slot:item.company="{ item }">
          <company-column :item="item" />
        </template>

        <template v-slot:item.status="{ item }">
          <status-column :item="item" />
        </template>

        <template v-slot:item.about="{ item }">
          <about-column :item="item" />
        </template>

        <template v-slot:item.users="{ item }">
          <users-column :item="item" />
        </template>

        <template v-slot:item.edit="{ item }">
          <v-btn icon small>
            <v-icon>{{ "mdi-" + item.edit }}</v-icon>
          </v-btn>
        </template>

        <template v-slot:item.delete="{ item }">
          <v-btn icon small>
            <v-icon>{{ "mdi-" + item.delete }}</v-icon>
          </v-btn>
        </template>

        <template v-slot:item.licenseUse="{ item }">
          <license-use-column :item="item" />
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
import tableData from "~/data/tableContent";
import CustomCheckbox from "~/components/common/CustomCheckbox.vue";
import CustomSearchTextField from "~/components/common/CustomSearchTextField.vue";
import DashboardTableFilters from "./Filters.vue";
import DashboardTableFooter from "./Footer.vue";
import CompanyColumn from "./CompanyColumn.vue";
import StatusColumn from "./StatusColumn.vue";
import AboutColumn from "./AboutColumn.vue";
import UsersColumn from "./UsersColumn.vue";
import LicenseUseColumn from "./LicenseUseColumn.vue";

export default {
  components: {
    CustomCheckbox,
    CustomSearchTextField,
    DashboardTableFilters,
    DashboardTableFooter,
    CompanyColumn,
    StatusColumn,
    AboutColumn,
    UsersColumn,
    LicenseUseColumn,
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
    setSelectedHeader() {
      if (this.selected.length > 0 && !this.selectedAll) {
        this.selected = [];
      } else {
        if (this.selectedAll) {
          this.selected = [];
        } else {
          const ss = this.tableContent.map((a) => a.company.name);
          for (let a of ss) {
            this.selected.push(a);
          }
        }
        this.selectedAll = !this.selectedAll;
      }
    },
    setSelected(item) {
      const value = this.selected.find((a) => a === item.company.name);
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
table tbody tr:nth-child(odd) {
  background: #f9fafb;
}

table tbody tr td {
  border: none !important;
  height: 72px !important;
}
</style>