<template>
  <q-layout view="lHh Lpr lFf">
    <!-- <q-header elevated class="glossy"> 
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="toggleDrawer"
          aria-label="Menu"
          icon="menu"
        />

        <q-toolbar-title> Quasar App </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header> -->

    <!-- <q-drawer v-model="leftDrawerOpen" show-if-above bordered class="bg-grey-2">
      <q-list>
        <q-item-label header>Essential Links</q-item-label>
        <q-item clickable tag="Router-Link" :to="{ name: 'home' }">
          <q-item-section avatar>
            <q-icon name="home" />
          </q-item-section>
          <q-item-section>
            <q-item-label>首頁</q-item-label>
            <q-item-label caption>Home Page</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="Router-Link" :to="{ name: 'product-list' }">
          <q-item-section avatar>
            <q-icon name="list" />
          </q-item-section>
          <q-item-section>
            <q-item-label>產品列表</q-item-label>
            <q-item-label caption>Product List</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="Router-Link" :to="{ name: 'create-product' }">
          <q-item-section avatar>
            <q-icon name="chat" />
          </q-item-section>
          <q-item-section>
            <q-item-label>新增商品</q-item-label>
            <q-item-label caption>Create Product</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="Router-Link" :to="{ name: 'user-info' }">
          <q-item-section avatar>
            <q-icon name="person" />
          </q-item-section>
          <q-item-section>
            <q-item-label>使用者資訊</q-item-label>
            <q-item-label caption>User Info</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="Router-Link" :to="{ name: 'api-test' }">
          <q-item-section avatar>
            <q-icon name="api" />
          </q-item-section>
          <q-item-section>
            <q-item-label>API 測試</q-item-label>
            <q-item-label caption>API Test</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer> -->
    <CqHeader
      :leftDrawerOpen="leftDrawerOpen"
      @switchMenu="switchMenu"
    ></CqHeader>
    <SlideMenu :leftDrawerOpen="leftDrawerOpen"></SlideMenu>

    <q-page-container>
      <router-view></router-view>
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from "vue";
import SlideMenu from "./views/layout/SlideMenu.vue";
import CqHeader from "./views/layout/CqHeader.vue";

const leftDrawerOpen = ref(false);

const toggleDrawer = () => {
  leftDrawerOpen.value = !leftDrawerOpen.value;
};

const switchMenu = () => {
  console.log("Hello");
  leftDrawerOpen.value = !leftDrawerOpen.value;
};
</script>
