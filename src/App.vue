<template>
  <!-- 2) passing total income as a prop -->
  <Header :totalIncome="state.totalIncome" />

  <!-- C) when we call this function it will take those props as params -->
  <Form @add-income="AddIncome" />
  <!-- either of these two work -->
  <!-- <Form v-on:add-income="AddIncome" /> -->
  <IncomeList :state="state" />
</template>

<script>
import { reactive, computed } from "vue";
import Header from "./components/Header";
import Form from "./components/Form";
import IncomeList from "./components/IncomeList";

export default {
  setup() {
    const state = reactive({
      income: [],
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

    // D) which we're passing in as "data"
    //  this data is what's being passed back up from our Form component
    function AddIncome(data) {
      // console.log(data);

      let d = data.date.split("-");
      let newD = new Date(d[0], d[1], d[2]);

      // E) assing this func's "state.income variable" as "all" (spread operator) the income we have and the second param (the object) is the data we passed
      state.income = [
        ...state.income,
        {
          id: Date.now(),
          desc: data.desc,
          value: parseInt(data.value),
          date: newD.getTime(),
        },
      ];
      console.log(state.income);
    }

    // 1) what we return here will be usable in our templates
    return {
      Header,
      Form,
      state,
      AddIncome,
      IncomeList,
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
