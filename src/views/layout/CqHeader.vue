<template>
  <q-header elevated class="glossy">
    <q-toolbar>
      <q-btn flat dense round @click="callBack" aria-label="Menu" icon="menu" />

      <q-toolbar-title> Quasar App </q-toolbar-title>

      <div>Quasar v{{ $q.version }}</div>
    </q-toolbar>
  </q-header>
</template>

<script setup>
import { defineProps, toRef, defineEmits } from "vue";

const props = defineProps({
  leftDrawerOpen: Boolean,
});

const leftDrawerOpen = toRef(props, "leftDrawerOpen");
const emit = defineEmits(["switchMenu"]);

const callBack = () => {
  console.log("====");
  emit("switchMenu");
};
</script>
