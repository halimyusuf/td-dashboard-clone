<template>
  <div>
    <div class="d-flex justify-space-between py-4 py-sm-6 px-2 align-center">
      <div class="d-none d-sm-flex">
        <div class="">
          <v-btn outlined class="cust-btn" color="#7F56D9">
            <div class="cust-btn-text">Previous</div>
          </v-btn>
        </div>
        <div class="ml-2">
          <v-btn outlined class="cust-btn" color="#7F56D9">
            <div class="cust-btn-text">Next</div>
          </v-btn>
        </div>
      </div>
      <div class="d-sm-none">
        <v-btn icon small color="#F9F5FF">
          <v-icon size="20" color="#667085">mdi-arrow-left</v-icon>
        </v-btn>
      </div>
      <div class="pagination-page">Page 1 of 10</div>
      <div class="d-sm-none">
        <v-btn icon small color="#F9F5FF">
          <v-icon size="20" color="#667085">mdi-arrow-right</v-icon>
        </v-btn>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
</style>