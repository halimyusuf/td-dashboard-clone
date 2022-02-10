<template>
  <div
    :class="`d-none  d-md-flex align-item-center ${firstLink ? '' : 'ml-5'}`"
  >
    <div
      v-for="(link, i) in navLinks"
      :key="link.label"
      :class="`px-2 ${
        firstLink && i === 0 ? 'mr-1' : 'mx-1'
      } py-2 body-2 nav-link ${currentLink === link.label ? 'active' : ''}`"
      @click="() => setCurrentLink(link.label)"
    >
      <div class="" style="font-size: 16px">{{ link.label }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["navLinks", "setCurrentLink", "currentLink", "firstLink"],
};
</script>

<style scoped>
.nav-link {
  cursor: pointer;
  border-radius: 6px;
}

.nav-link.active {
  background-color: #f9fafb;
}
</style>