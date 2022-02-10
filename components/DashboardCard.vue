<template>
  <v-card outlined class="m-card">
    <div class="d-flex justify-space-between align-center">
      <div class="m-card-label">{{ label }}</div>
      <div>
        <v-icon color="#98A2B3" size="20">mdi-dots-vertical</v-icon>
      </div>
    </div>

    <div class="d-flex justify-space-between mt-6">
      <div class="mr-7">
        <div class="m-card-value">
          {{ parseInt(value).toLocaleString() }}
        </div>
        <template v-if="increase">
          <div class="card-footer-increase">
            <div class="mr-1">
              <v-icon size="20" color="#12B76A">mdi-arrow-up</v-icon>
            </div>
            <div class="mr-2">{{ percentChange }}%</div>
            <div>vs last month</div>
          </div>
        </template>

        <template v-else>
          <div class="card-footer-decrease">
            <div class="mr-1">
              <v-icon size="20" color="#F04438">mdi-arrow-down</v-icon>
            </div>
            <div class="mr-2">{{ percentChange }}%</div>
            <div>vs last month</div>
          </div>
        </template>
      </div>
      <div>
        <template v-if="increase">
          <div class="card-img-cont">
            <div class="card-img">
              <img class="" src="../assets/Background base.svg" />
            </div>
            <div class="card-img">
              <img class="" src="../assets/IncreaseLine.svg" />
            </div>
          </div>
        </template>
        <template v-else>
          <div class="card-img-cont">
            <div class="card-img">
              <img class="" src="../assets/Background base (1).svg" />
            </div>
            <div class="card-img">
              <img class="" src="../assets/DecreaseLine.svg" />
            </div>
          </div>
        </template>
      </div>
    </div>
  </v-card>
</template>

<script>
export default {
  props: ["label", "value", "percentChange", "increase"],
  data() {
    return {};
  },
};
</script>

<style>
.m-card {
  padding: 24px;
}

.m-card-label {
  font-size: 16px;
  font-weight: 500;
  line-height: 24px;
}

.m-card-value {
  font-size: 36px;
  font-weight: 600;
  line-height: 44px;
  letter-spacing: -0.02em;
  margin: 0 5px 0 0;
}

.card-img-cont {
  background: #ffffff;
  position: relative;
  width: 128px;
  height: 64px;
  max-width: 100%;
}

.card-img {
  position: absolute;
  width: 128px;
  height: 64px;
  max-width: 100%;
}

.card-img img {
  width: 100%;
  height: 100%;
}

.card-img-decrease {
  /* background: url("../assets/Background base (1).svg"),
    linear-gradient(180deg, rgba(255, 255, 255, 0) 64.12%, #ffffff 100%); */
}

/* .card-img-bg {
  background: ;
} */
.card-footer-increase,
.card-footer-decrease {
  display: flex;
  margin-top: 20px;
  align-items: center;
  flex-wrap: wrap;
}

.card-footer-decrease div:nth-child(2),
.card-footer-increase div:nth-child(2) {
  font-size: 14px;
  font-weight: 500;
}

.card-footer-decrease div:nth-child(2) {
  color: #b42318;
}

.card-footer-increase div:nth-child(2) {
  color: #027a48;
}

.card-footer-decrease div:nth-child(3),
.card-footer-increase div:nth-child(3) {
  font-size: 14px;
  font-weight: 500;
  color: #667085;
}
</style>