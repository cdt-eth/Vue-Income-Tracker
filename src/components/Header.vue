<template>
  <header>
    <h1>Income Tracker</h1>
    <!-- 4) we create a template with our passed down total income prop value -->
    <div class="total-income">${{ totalIncome }}</div>
  </header>
</template>

<script>
export default {
  // 3) receiving the total income prop passed from our App component
  // declaring its type a Number
  props: {
    totalIncome: Number,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 30px;
  background-color: #313131;
  border-bottom: 5px solid #ffce00;
}
header h1 {
  color: #eee;
  font-size: 28px;
}
header .total-income {
  font-family: "Fira Code", "Fira Sans", sans-serif;
  background-color: #ffce00;
  color: #fff;
  font-size: 20px;
  font-weight: 900;
  padding: 5px 10px;
  min-width: 100px;
  text-align: center;
  border-radius: 8px;
  box-shadow: inset 0px 0px 6px rgba(0, 0, 0, 0.25);
  text-shadow: 0px 3px 3px rgba(0, 0, 0, 0.25);
}
</style>
