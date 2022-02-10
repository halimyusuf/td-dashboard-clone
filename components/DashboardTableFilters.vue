<template>
  <div>
    <div
      class="
        d-block
        table-ctrls
        d-sm-flex
        justify-space-between
        flex-row-reverse
      "
    >
      <div>
        <div class="search-cont ml-sm-5 d-xs-none">
          <custom-search-text-field placeholder="Searchhh" />
        </div>
      </div>
      <div class="d-block d-sm-flex flex-wrap">
        <div class="d-none d-md-flex mt-2 mt-sm-1">
          <div class="mr-3" v-for="filter in filters" :key="filter.filter">
            <v-btn class="cust-pry-btn" depressed color="#F9F5FF">
              <div class="cust-pry-btn-text">{{ filter.filter }}</div>
              <v-icon color="#6941C6">mdi-close</v-icon>
            </v-btn>
          </div>
        </div>

        <div class="mr-sm-3 my-4 my-sm-1">
          <v-btn outlined class="cust-btn" color="#7F56D9" block>
            <v-icon color="#344054">mdi-filter-variant</v-icon>
            <div class="ml-2 cust-btn-text">More filters</div>
          </v-btn>
        </div>
      </div>
    </div>
    <div class="d-flex d-md-none mt-2 mt-sm-1">
      <div class="mr-3" v-for="filter in filters" :key="filter.filter">
        <v-btn class="cust-pry-btn" depressed color="#F9F5FF" small>
          <div class="cust-pry-btn-text">{{ filter.filter }}</div>
          <v-icon color="#6941C6">mdi-close</v-icon>
        </v-btn>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["filters"],
};
</script>

<style >
@media screen and (max-width: 600px) {
  .search-cont {
    width: 600px !important;
    max-width: 100%;
  }
}
</style>