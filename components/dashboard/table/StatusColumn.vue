<template>
  <div>
    <v-chip :color="isCustomer(item.status) ? '#ECFDF3' : '#F2F4F7'" small>
      <div :style="`${isCustomer(item.status) ? 'color: #027a48' : '#344054'}`">
        {{ item.status }}
      </div>
    </v-chip>
  </div>
</template>

<script>
export default {
  props: ["item"],
  methods: {
    isCustomer(status) {
      return status.toLowerCase() === "customer";
    },
  },
};
</script>

<style>
</style>