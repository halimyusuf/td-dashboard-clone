<template>
  <div>
    <div style="width: 88px">
      <v-progress-linear
        height="8px"
        color="#7F56D9"
        rounded
        :value="item.licenseUse * 10"
        background-color="#F9F5FF"
      ></v-progress-linear>
    </div>
    <div>
      <v-icon>{{ "mdi-" + item.licenseUse }}</v-icon>
    </div>
  </div>
</template>

<script>
export default {
  props: ["item"],
};
</script>

<style>
</style>