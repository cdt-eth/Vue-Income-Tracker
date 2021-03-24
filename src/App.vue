<template>
  <!-- 2) passing total income as a prop -->
  <Header :totalIncome="state.totalIncome" />
</template>

<script>
import { reactive, computed } from "vue";
import Header from "./components/Header";

export default {
  setup() {
    const state = reactive({
      income: [
        {
          value: 400,
        },
        {
          value: 500,
        },
      ],
      totalIncome: computed(() => {
        let temp = 0;

        // making sure we actually have income
        if (state.income.length > 0) {
          // we'll loop through the array of income amounts
          for (let i = 0; i < state.income.length; i++) {
            // and add them up for a total, assigned to temp
            temp += state.income[i].value;
          }
        }

        return temp;
      }),
    });

    // 1) what we return here will be usable in our templates
    return {
      Header,
      state,
    };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Fira Sans", sans-serif;
}

body {
  background: #eee;
}
</style>
