<template>
  <div class="daily-item">
    <div class="day-of-week">{{ getDayOfWeek }}</div>
    <div class="date">{{ getDateStr }}</div>
    <img
      class="icon"
      :src="require('../assets/images/' + daily_forecast.cond_code_d + '.svg')"
    />
    <div class="text">{{ daily_forecast.cond_txt_d }}</div>
    <div class="temp">
      <span class="max">{{ daily_forecast.tmp_max }}˚</span>
      <span class="split"></span>
      <span class="min">{{ daily_forecast.tmp_min }}˚</span>
    </div>
  </div>
</template>
<script>
import moment from "moment";
export default {
  name: "DailyItem",
  props: {
    daily_forecast: {
      type: Object,
      default: () => ({})
    }
  },
  computed: {
    getDateStr: function() {
      moment.locale("zh-CN");
      let dt = moment(this.daily_forecast.date, "YYYY-MM-DD");
      return dt.format("MM/DD");
    },
    getDayOfWeek: function() {
      moment.locale("zh-CN");
      let dt = moment(this.daily_forecast.date, "YYYY-MM-DD");
      let today = dt.isSame(new Date(), "day");
      let tomor = dt.isSame(moment(new Date()).add(1, "days"), "day");
      if (today) {
        return "今天";
      } else if (tomor) {
        return "明天";
      } else {
        return dt.format("dddd");
      }
    }
  }
};
</script>

<style scoped lang="scss">
@import "../assets/css/common.scss";

.daily-item {
  display: flex;
  flex: 1;
  flex-direction: column;
  align-items: center;
  .day-of-week {
    font-size: 2.8rem;
    color: #ffffff;
    font-weight: 400;
  }
  .date {
    margin-top: 2rem;
    color: #ffffff7f;
    font-size: 2.4rem;
    background-color: #00000019;
    border-radius: 2.4rem;
  }
  .icon {
    margin-top: 5.6rem;
    width: 6rem;
    height: 6rem;
  }
  .text {
    margin-top: 3.2rem;
    margin-bottom: 2rem;
    font-size: 2rem;
  }
  .temp {
    font-size: 2.7rem;
    font-weight: bold;
    display: flex;
    flex-direction: column;
    width: 7rem;
    align-items: center;
    .split {
      height: 2px;
      margin: 0.5rem 0;
      background: #000000;
      opacity: 0.1;
      width: 100%;
    }
    .min {
      opacity: 0.5;
    }
  }
}
</style>
