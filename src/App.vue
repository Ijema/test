<template>
  <n-message-provider>
    <CustomLayout>
      <CustomTable />
    </CustomLayout>
  </n-message-provider>
</template>

<script setup>
import { NMessageProvider } from 'naive-ui';
import CustomLayout from './components/CustomLayout/CustomLayout.vue';
import CustomTable from './components/CustomTable.vue';
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
