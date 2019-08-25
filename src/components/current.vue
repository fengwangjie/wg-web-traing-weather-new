<template>
  <div class="main">
    <div class="icon">
      <img src="../assets/images/101.svg" />
    </div>
    <div class="detail">
      <div class="left">
        <span class="temp-now">23˚</span>
      </div>
      <div class="right">
        <span class="text">中雨</span>
        <div class="temp">
          <span class="temp-hign">12˚</span>
          <span class="temp-low">23˚</span>
        </div>
      </div>
    </div>
    <span class="air-info">空气质量优</span>
  </div>
</template>

<script>
export default {
  name: "CurrentWeather",
  props: {
    info: {
      type: Object,
      default: () => ({})
    }
  }
};
</script>

<style scoped lang="scss">
@import "../assets/css/common.scss";
.main {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 2rem 2.5rem;
  .icon image {
    width: 8rem;
    height: 8rem;
  }
  .detail {
    font-size: 4rem;
    margin: 1rem 0;
    display: flex;
    justify-items: flex-end;

    .left {
      display: flex;
      align-items: flex-end;

      .temp-now {
        font-size: 15rem;
      }
    }

    .right {
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      padding-bottom: 3.5rem;
      .temp {
        .temp-low {
          opacity: 0.5;
        }
      }
    }
  }
  .air-info {
    font-size: 2.4rem;
    background: linear-gradient(to right, #b5eb45, #7ed321);
    border-radius: 0.3rem;
    padding: 1.6rem;
  }
}
</style>
