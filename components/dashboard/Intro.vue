<template>
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
</template>

<script>
export default {};
</script>

<style>
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
</style>