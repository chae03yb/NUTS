<template>
  <div>
    <div v-if="loading">로딩 중...</div>
    <div v-else>
      <h2>오늘의 점심</h2>
      <div class="menu_box" v-for="(menu, index) in lunchMenus" :key="index">
        <pre>{{ menu }}</pre>
      </div>

      <h2>오늘의 저녁</h2>
      <div class="menu_box" v-for="(menu, index) in dinnerMenus" :key="index">
        <pre>{{ menu }}</pre>
      </div>
      <div v-if="error">{{ error }}</div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

var date = new Date();
var year = date.getFullYear().toString().slice(-2);
var month = (date.getMonth() + 1).toString().padStart(2, "0");
var day = date.getDate().toString().padStart(2, "0");

console.log(year + month + day);

export default {
  data() {
    return {
      loading: true,
      lunchMenus: [],
      dinnerMenus: [],
      error: null,
    };
  },
  methods: {
    async fetchMenus() {
      try {
        const lunchResponse = await axios.get(
          "	https://open.neis.go.kr/hub/mealServiceDietInfo?ATPT_OFCDC_SC_CODE=N10&SD_SCHUL_CODE=814026&MLSV_YMD=${MLSV_YMD}",
          {
            params: {
              KEY: "24f66fdc96aa43d180bceac32e6205f7", // 공공데이터 포털에서 발급받은 API 키
              Type: "json", // 응답 형식
              ATPT_OFCDC_SC_CODE: "N10", // 시도교육청코드 (예: 충청남도교육청)
              SD_SCHUL_CODE: "8140246", // 학교 코드 (예: 천안오성고)
              MMEAL_SC_CODE: "2", // 급식 유형 코드 (2: 중식)
              MLSV_YMD: year + month + day, // 오늘 날짜
            },
          }
        );
        console.log("API 응답:", lunchResponse);
        if (lunchResponse.data.mealServiceDietInfo) {
          this.lunchMenus = lunchResponse.data.mealServiceDietInfo[1].row.map(
            (menu) => menu.DDISH_NM.replace(/<br\/>/g, "\n")
          );
        } else {
          this.error = "No Lunch meal service data found";
        }

        const dinnerResponse = await axios.get(
          "	https://open.neis.go.kr/hub/mealServiceDietInfo?ATPT_OFCDC_SC_CODE=N10&SD_SCHUL_CODE=814026&MLSV_YMD=${MLSV_YMD}",
          {
            params: {
              KEY: "24f66fdc96aa43d180bceac32e6205f7", // 공공데이터 포털에서 발급받은 API 키
              Type: "json", // 응답 형식
              ATPT_OFCDC_SC_CODE: "N10", // 시도교육청코드 (예: 충청남도교육청)
              SD_SCHUL_CODE: "8140246", // 학교 코드 (예: 천안오성고)
              MMEAL_SC_CODE: "3", // 급식 유형 코드 (3: 석식)
              MLSV_YMD: year + month + day, // 오늘 날짜
            },
          }
        );
        console.log("API 응답:", dinnerResponse);
        if (dinnerResponse.data.mealServiceDietInfo) {
          this.dinnerMenus = dinnerResponse.data.mealServiceDietInfo[1].row.map(
            (menu) => menu.DDISH_NM.replace(/<br\/>/g, "\n")
          );
        } else {
          this.error = "No Dinner meal service data found";
        }
      } catch (error) {
        console.error("API request error:", error);
        this.error = `API 요청 중 오류 발생: ${error.message}`;
      } finally {
        this.loading = false;
      }
    },
  },
  mounted() {
    this.fetchMenus();
  },
};
</script>

<style scoped>
h2 {
  font-size: 24px;
  margin-bottom: 20px;
  margin-top: 50px;
}
.container {
  padding: 20px;
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
}

.menu_box {
  border: 1px solid black;
  padding: 10px;
  margin: 10px 0;
  border-radius: 4px;
  background-color: #f9f9f9;
  text-align: left;
  white-space: pre-line;
}

.error {
  color: red;
  margin-top: 20px;
}
</style>
