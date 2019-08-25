<template>
  <div class="item">
    <img
      class="'icon"
      :src="require('../assets/images/ic_weather_' + iconName + '.png')"
    />
    <div class="label">{{ label }}</div>
    <div class="val">{{ val }}</div>
  </div>
</template>

<script>
export default {
  name: "detail",
  props: {
    iconName: {
      type: String,
      default: ""
    },
    label: {
      type: String,
      default: ""
    },
    val: {
      type: String,
      default: ""
    }
  },
  computed: {
    iconSrc: function() {
      return "../assets/images/ic_weather_smail_sun.png";
    }
  }
};
</script>

<style scoped lang="scss">
@import "../assets/css/common.scss";

.item {
  padding: 1rem;
  width: 33%;
  height: 100%;
  margin-right: 2.5rem;
  border-radius: 0.8rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: linear-gradient(to right, #00000026, #00000019);
  .icon {
  }

  .label {
    font-size: 2rem;
    margin-top: 1rem;
  }

  .val {
    margin-top: 0.8rem;
    font-size: 2rem;
    color: #ffffff;
  }
}
</style>
