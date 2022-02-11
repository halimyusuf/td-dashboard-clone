<template>
  <div class="d-flex">
    <div class="mr-3">
      <img :src="require(`~/assets/company logo/${item.company.logo}`)" />
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

<script>
export default {
  props: ["item"],
};
</script>

<style>
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