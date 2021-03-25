<template>
  <div class="income-list">
    <IncomeItem v-for="data in state.income" :key="data.id" :income="data" />
  </div>
</template>

<script>
import IncomeItem from "./IncomeItem";

export default {
  props: {
    state: Object,
  },
  setup() {
    return {
      IncomeItem,
    };
  },
};
</script>

<style scoped>
.income-list {
  margin-top: 30px;
  padding: 15px;
}
</style>
