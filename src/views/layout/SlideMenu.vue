<template>
  <div>
    <q-drawer v-if="leftDrawerOpen" show-if-above bordered class="bg-grey-2">
      <q-list>
        <q-item-label header>Links</q-item-label>
        <div v-for="nav in navs" :key="nav.id">
          <q-item clickable tag="router-link" :to="{ name: nav.name }">
            <q-item-section avatar>
              <q-icon :name="nav.icon" />
            </q-item-section>
            <q-item-section>
              <q-item-label>{{ nav.title }}</q-item-label>
              <q-item-label caption>{{ nav.secTitle }}</q-item-label>
            </q-item-section>
          </q-item>
        </div>
      </q-list>
    </q-drawer>
  </div>
</template>

<script setup>
import axios from "axios";
import { defineProps, toRef, onMounted, ref } from "vue";

const navs = ref([]);

onMounted(() =>
  axios.get("/api/navs.json").then(({ data }) => {
    navs.value = data;
  })
);

const props = defineProps({
  leftDrawerOpen: Boolean,
});

const leftDrawerOpen = toRef(props, "leftDrawerOpen");
</script>
