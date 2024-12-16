<template>
  <div>
    <q-drawer v-if="leftDrawerOpen" show-if-above bordered class="bg-grey-2">
      <q-list>
        <q-item-label header>Links</q-item-label>
        <q-item clickable tag="router-Link" :to="{ name: 'home' }">
          <q-item-section avatar>
            <q-icon name="home" />
          </q-item-section>
          <q-item-section>
            <q-item-label>首頁</q-item-label>
            <q-item-label caption>Home Page</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="router-Link" :to="{ name: 'product-list' }">
          <q-item-section avatar>
            <q-icon name="list" />
          </q-item-section>
          <q-item-section>
            <q-item-label>產品列表</q-item-label>
            <q-item-label caption>Product List</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="router-Link" :to="{ name: 'create-product' }">
          <q-item-section avatar>
            <q-icon name="chat" />
          </q-item-section>
          <q-item-section>
            <q-item-label>新增商品</q-item-label>
            <q-item-label caption>Create Product</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="router-Link" :to="{ name: 'user-info' }">
          <q-item-section avatar>
            <q-icon name="person" />
          </q-item-section>
          <q-item-section>
            <q-item-label>使用者資訊</q-item-label>
            <q-item-label caption>User Info</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="router-Link" :to="{ name: 'api-test' }">
          <q-item-section avatar>
            <q-icon name="api" />
          </q-item-section>
          <q-item-section>
            <q-item-label>API 測試</q-item-label>
            <q-item-label caption>API Test</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="router-Link" :to="{ name: 'PostCode' }">
          <q-item-section avatar>
            <q-icon name="api" />
          </q-item-section>
          <q-item-section>
            <q-item-label>PostCode</q-item-label>
            <q-item-label caption>PostCode</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>
  </div>
</template>

<script setup>
import { defineProps, toRef } from "vue";

const props = defineProps({
  leftDrawerOpen: Boolean,
});

const leftDrawerOpen = toRef(props, "leftDrawerOpen");
</script>
