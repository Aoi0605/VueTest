<template>
  <div class="q-pa-md" style="max-width: 600px">
    <div>
      <p style="font-size: 20px">產品表單</p>
      <p>請輸入產品資訊</p>
    </div>
    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
      <q-input
        filled
        type="text"
        v-model="productName"
        label="產品名稱"
        lazy-rules
        :rules="[(val) => (val !== null && val !== '') || '請輸入產品名稱']"
      />

      <q-input
        filled
        type="number"
        v-model="price"
        label="價格"
        lazy-rules
        :rules="[(val) => (val !== null && val !== '') || '請輸入產品價格']"
      />

      <q-input
        filled
        type="textarea"
        v-model="describe"
        label="產品描述"
        lazy-rules
        :rules="[(val) => (val !== null && val !== '') || '請輸入產品描述']"
      />

      <div>
        <q-btn label="Submit" type="submit" color="primary" />
        <q-btn
          label="Reset"
          type="reset"
          color="primary"
          flat
          class="q-ml-sm"
        />
      </div>
    </q-form>
  </div>
</template>

<script>
import { useQuasar } from "quasar";
import { ref } from "vue";

export default {
  setup() {
    const $q = useQuasar();

    // 表單變數
    const productName = ref(null);
    const price = ref(null);
    const describe = ref(null);

    // 提交邏輯
    const onSubmit = () => {
      $q.notify({
        color: "green-4",
        textColor: "white",
        icon: "cloud_done",
        message: "表單已提交",
      });
    };

    // 重設邏輯
    const onReset = () => {
      productName.value = null;
      price.value = null;
      describe.value = null;
    };

    return {
      productName,
      price,
      describe,
      onSubmit,
      onReset,
    };
  },
};
</script>
