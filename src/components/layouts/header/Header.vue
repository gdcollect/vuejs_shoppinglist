<template>
  <header class="header">
    <h1>{{ heading }}</h1>
  </header>
</template>


<script>
export default {
  name: "header",
  props: {
    heading: String
  }
};
</script>


<style scoped>
h1 {
  margin: 0;
  padding: 1rem;
  text-align: center;
  color: #f4f4f4;
  background: rgb(12, 110, 101);
  text-transform: uppercase;
  border-bottom: 1px solid #fff;
}
</style>