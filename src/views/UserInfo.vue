<template>
  <q-page padding>
    <q-toolbar>
      <q-toolbar-title>用戶資訊</q-toolbar-title>
      <q-btn label="編輯" color="primary" @click="editMode = !editMode" />
    </q-toolbar>

    <!-- 用戶資訊卡片 -->

    <q-card class="q-mb-md">
      <div v-for="user in users" :key="user.id">
        <q-card-section>
          <div class="text-h6">基本資料</div>

          <q-separator />

          <!-- 用戶姓名 -->
          <q-input
            v-model="user.name"
            label="姓名"
            :disabled="!editMode"
            outlined
            dense
          />

          <!-- 用戶電子郵件 -->
          <q-input
            v-model="user.email"
            label="電子郵件"
            :disabled="!editMode"
            outlined
            dense
          />

          <!-- 用戶角色 -->
          <q-select
            v-model="user.role"
            label="角色"
            :options="users.role"
            :disable="!editMode"
            outlined
            dense
          />

          <!-- 註冊日期 -->
          <q-input
            v-model="user.registrationDate"
            label="註冊日期"
            :disabled="true"
            outlined
            dense
          />
        </q-card-section>
      </div>

      <!-- 保存與取消按鈕 -->
      <q-card-actions align="right">
        <q-btn
          label="取消"
          color="negative"
          flat
          @click="cancelEdit"
          v-if="editMode"
        />
        <q-btn
          label="保存"
          color="positive"
          flat
          @click="saveUserInfo"
          v-if="editMode"
        />
      </q-card-actions>
    </q-card>
  </q-page>
</template>

<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";
const users = ref([]);

// 編輯模式開關
const editMode = ref(false);

onMounted(() =>
  axios.get("/api/userInfo.json").then(({ data }) => {
    users.value = data;
  })
);

// 保存用戶資訊
const saveUserInfo = () => {
  // 這裡可以添加保存邏輯，如提交 API 請求
  console.log("保存用戶資訊", users.value);
  editMode.value = false;
};

// 取消編輯
const cancelEdit = () => {
  // 恢復編輯前的資料
  // user.value = {
  //   name: "王小明",
  //   email: "xiaoming@example.com",
  //   role: "會員",
  //   registrationDate: "2023-05-01",
  // };
  editMode.value = false;
};
</script>
