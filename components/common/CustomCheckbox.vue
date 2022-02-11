<template>
  <div :class="`tick-cont ${valid || hasSelected ? 'ticked' : ''}`">
    <v-icon v-if="hasSelected" size="15" color="#7F56D9"> mdi-minus </v-icon>
    <v-icon v-else-if="valid" size="15" color="#7F56D9"> mdi-check </v-icon>
  </div>
</template>

<script>
export default {
  props: ["data", "selected", "header", "selectedAll"],
  computed: {
    valid() {
      if (this.header) {
        return this.selectedAll;
      }
      return (
        this.selected.find((a) => a === this.data.item.company.name) !==
          undefined || this.selectedAll
      );
    },
    hasSelected() {
      return this.header && this.selected.length > 0;
    },
  },
};
</script>

<style>
.tick-cont {
  border: 1px solid #d0d5dd;
  box-sizing: border-box;
  border-radius: 6px;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 20px;
  height: 20px;
}

.tick-cont.ticked {
  border: 1px solid #7f56d9;
  background: #f9f5ff;
}
</style>