<template>
  <div class="item">
    <span class="label">{{ label }}</span>
    <span class="val">{{ val }}</span>
    <span class="unit">({{ unit }})</span>
  </div>
</template>
<script>
export default {
  name: "air-info-item",
  props: {
    label: {
      type: String,
      default: ""
    },
    val: {
      type: String,
      default: ""
    },
    unit: {
      type: String,
      default: ""
    }
  }
};
</script>
<style scoped lang="scss">
@import "../assets/css/common.scss";
.item {
  display: flex;
  flex-direction: column;
  text-align: center;
  justify-content: center;
  align-items: center;
  .label {
    font-size: 2.4rem;
    color: #ffffff7f;
    margin-bottom: 1.5rem;
  }

  .val {
    font-size: 2rem;
    color: #ffffff;
    font-weight: bold;
    margin-bottom: 1.5rem;
  }
  .unit {
    font-size: 2rem;
    color: #ffffff7f;
    margin-top: 0.6rem;
  }
}
</style>
