<template>
  <div class="about-text">
    <div>{{ item.about.text1 }}</div>
    <div>{{ item.about.text2 }}</div>
  </div>
</template>

<script>
export default {
  props: ["item"],
};
</script>

<style>
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
</style>