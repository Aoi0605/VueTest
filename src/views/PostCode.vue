<template>
  <label
    >郵遞區號
    <input
      type="text"
      v-model="postalCode"
      placeholder="郵遞區號"
      @blur="findLocationByPostalCode"
    />
  </label>

  <select v-model="selectedCity" @change="updateDistricts">
    <option value="">請選擇區域</option>
    <option value="台北市">台北市</option>
    <option value="基隆市">基隆市</option>
    <option value="連江縣">連江縣</option>
  </select>

  <!-- 區域選單 -->
  <select
    v-model="selectedDistrict"
    @change="updatePostalCode"
    :disabled="districts.length === 0"
  >
    <option value="">請選擇區域</option>
    <option
      v-for="district in districts"
      :key="district.name"
      :value="district.name"
    >
      {{ district.name }}
    </option>
  </select>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    // 定義縣市對應的區域資料
    const districtsData = {
      台北市: [
        { name: "中正區", postalCode: "100" },
        { name: "大同區", postalCode: "103" },
        { name: "中山區", postalCode: "104" },
        { name: "松山區", postalCode: "105" },
        { name: "大安區", postalCode: "106" },
        { name: "萬華區", postalCode: "108" },
        { name: "信義區", postalCode: "110" },
        { name: "士林區", postalCode: "111" },
        { name: "北投區", postalCode: "112" },
        { name: "內湖區", postalCode: "114" },
        { name: "南港區", postalCode: "115" },
        { name: "文山區", postalCode: "116" },
      ],
      基隆市: [
        { name: "仁愛區", postalCode: "200" },
        { name: "信義區", postalCode: "201" },
        { name: "中正區", postalCode: "202" },
        { name: "中山區", postalCode: "203" },
        { name: "安樂區", postalCode: "204" },
        { name: "暖暖區", postalCode: "205" },
        { name: "七堵區", postalCode: "206" },
      ],
      連江縣: [
        { name: "南竿", postalCode: "209" },
        { name: "北竿", postalCode: "210" },
        { name: "莒光", postalCode: "211" },
        { name: "東引", postalCode: "212" },
      ],
    };

    const selectedCity = ref(""); // 當前選中的縣市
    const selectedDistrict = ref(""); // 當前選中的區域
    const districts = ref([]); // 動態更新的區域選單
    const postalCode = ref(""); // 當前郵遞區號

    // 當縣市改變時更新區域選單
    const updateDistricts = () => {
      selectedDistrict.value = ""; // 清空區域的選擇
      postalCode.value = ""; // 清空郵遞區號
      districts.value = districtsData[selectedCity.value] || []; // 動態設定區域選項
    };

    // 當區域改變時更新郵遞區號
    const updatePostalCode = () => {
      const district = districts.value.find(
        (d) => d.name === selectedDistrict.value
      );
      postalCode.value = district ? district.postalCode : "";
    };

    // 根據郵遞區號找到縣市與區域
    const findLocationByPostalCode = () => {
      let foundCity = "";
      let foundDistrict = "";

      // 遍歷所有縣市和區域資料
      for (const city in districtsData) {
        const district = districtsData[city].find(
          (d) => d.postalCode === postalCode.value
        );
        if (district) {
          foundCity = city;
          foundDistrict = district.name;
        }
      }

      // 更新縣市與區域選擇
      if (foundCity) {
        selectedCity.value = foundCity;
        updateDistricts(); // 更新區域列表
        selectedDistrict.value = foundDistrict;
      } else {
        selectedCity.value = "";
        selectedDistrict.value = "";
        districts.value = [];
      }
    };

    return {
      selectedCity,
      selectedDistrict,
      postalCode,
      districts,
      updateDistricts,
      updatePostalCode,
      findLocationByPostalCode,
    };
  },
};
</script>
