<template>
  <div class="container">
    <div class="title">
      <span>天气</span>
    </div>
    <div class="content">
      <div class="left">
        <current-weather class="current"></current-weather>
        <div class="detail">
          <weather-detail
            v-for="item in weatherDetail"
            :key="item.label"
            :iconName="item.iconName"
            :label="item.label"
            :val="item.val"
          />
        </div>
      </div>
      <div class="right">
        <div class="daily-forecast">
          <daily-item
            v-for="forecast in daily_forecast"
            :key="forecast.date"
            :daily_forecast="forecast"
          ></daily-item>
        </div>
        <div class="air-detail">
          <air-info-item
            v-for="item in airInfo"
            :key="item.label"
            :label="item.label"
            :val="item.val"
            :unit="item.unit"
          ></air-info-item>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import CurrentWeather from "./components/current";
import DailyItem from "./components/dailyItem";
import AirInfoItem from "./components/airInfoItem";
import weatherDetail from "./components/weatherDetail";
export default {
  name: "App",
  components: {
    CurrentWeather,
    DailyItem,
    AirInfoItem,
    weatherDetail
  },
  data: function() {
    return {
      weatherDetail: [
        { iconName: "wind", label: "东南风", val: "1级" },
        { iconName: "humidity", label: "湿度", val: "20%" },
        { iconName: "small_sun", label: "UV", val: "弱" }
      ],
      airInfo: [
        { label: "CO", val: "34/94", unit: "PPM" },
        { label: "CO2", val: "10/24", unit: "PPM" },
        { label: "PM2.5", val: "17/98", unit: "PPM" },
        { label: "PM10", val: "24/56", unit: "PPM" }
      ],
      daily_forecast: [
        {
          cond_code_d: "101",
          cond_code_n: "101",
          cond_txt_d: "多云",
          cond_txt_n: "多云",
          date: "2019-08-25",
          hum: "67",
          mr: "00:29",
          ms: "14:56",
          pcpn: "1.0",
          pop: "55",
          pres: "957",
          sr: "06:13",
          ss: "19:18",
          tmp_max: "32",
          tmp_min: "23"
        },
        {
          cond_code_d: "305",
          cond_code_n: "305",
          cond_txt_d: "小雨",
          cond_txt_n: "小雨",
          date: "2019-08-26",
          hum: "82",
          mr: "01:17",
          ms: "15:58",
          pcpn: "9.1",
          pop: "76",
          pres: "961",
          sr: "06:13",
          ss: "19:17",
          tmp_max: "31",
          tmp_min: "22"
        },
        {
          cond_code_d: "104",
          cond_code_n: "100",
          cond_txt_d: "阴",
          cond_txt_n: "晴",
          date: "2019-08-27",
          hum: "64",
          mr: "02:13",
          ms: "16:57",
          pcpn: "0.0",
          pop: "25",
          pres: "963",
          sr: "06:14",
          ss: "19:15",
          tmp_max: "27",
          tmp_min: "19"
        },
        {
          cond_code_d: "100",
          cond_code_n: "100",
          cond_txt_d: "晴",
          cond_txt_n: "晴",
          date: "2019-08-28",
          hum: "32",
          mr: "03:17",
          ms: "17:52",
          pcpn: "0.0",
          pop: "25",
          pres: "962",
          sr: "06:15",
          ss: "19:14",
          tmp_max: "28",
          tmp_min: "15"
        },
        {
          cond_code_d: "100",
          cond_code_n: "101",
          cond_txt_d: "晴",
          cond_txt_n: "多云",
          date: "2019-08-29",
          hum: "30",
          mr: "04:26",
          ms: "18:42",
          pcpn: "0.0",
          pop: "1",
          pres: "960",
          sr: "06:15",
          ss: "19:13",
          tmp_max: "26",
          tmp_min: "15"
        },
        {
          cond_code_d: "101",
          cond_code_n: "101",
          cond_txt_d: "多云",
          cond_txt_n: "多云",
          date: "2019-08-30",
          hum: "31",
          mr: "05:39",
          ms: "19:27",
          pcpn: "0.0",
          pop: "0",
          pres: "960",
          sr: "06:16",
          ss: "19:11",
          tmp_max: "26",
          tmp_min: "14"
        },
        {
          cond_code_d: "100",
          cond_code_n: "100",
          cond_txt_d: "晴",
          cond_txt_n: "晴",
          date: "2019-08-31",
          hum: "43",
          mr: "06:51",
          ms: "20:07",
          pcpn: "0.0",
          pop: "0",
          pres: "961",
          sr: "06:17",
          ss: "19:10",
          tmp_max: "29",
          tmp_min: "16"
        }
      ]
    };
  }
};
</script>

<style scoped lang="scss">
.container {
  background: white url("./assets/images/bg_rain.png") no-repeat fixed center;
  color: #ffffff;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 3.2rem;
  width: calc(100% - 6.4rem);
  height: calc(100% - 6.4rem);

  .title {
    display: flex;
    align-items: center;
    margin-bottom: 2rem;
    height: 3.2rem;
    span {
      color: #fff;
      font-size: 3.2rem;
      font-weight: bold;
    }
  }

  .content {
    display: flex;
    flex-direction: row;
    width: calc(100% - 6.4rem);
    flex-flow: 1;
    .left {
      flex-grow: 3;
      display: flex;
      flex-direction: column;
      .current {
        flex: 1;
      }
      .detail {
        display: flex;
        flex-direction: row;
        flex-wrap: nowrap;
        margin-right: 2rem;
        justify-content: space-between;
      }
    }
  }
  .right {
    flex-grow: 5;
    display: flex;
    flex-direction: column;
    .daily-forecast {
      flex: 1;
      display: flex;
      flex-direction: row;
      padding: 2rem 2.5rem;
      border-radius: 0.8rem;
      background: linear-gradient(to right, #00000026, #00000019);
    }
    .air-detail {
      display: flex;
      margin-top: 2rem;
      padding: 2rem 2.5rem;
      border-radius: 0.8rem;
      justify-content: space-around;
      background: linear-gradient(to right, #00000026, #00000019);
      align-items: center;
    }
  }
}
</style>
