<template>
  <div id="headerTotal">
    <h1>
      Valor Total R$<spam>{{ valorTotal }}</spam>
    </h1>
  </div>
</template>
<script>
export default {
  name: "HeaderList",
  data: () => ({
  }),
  props: {
    tabForm: null,
    valorTotal: null,
  }
};
</script>
<style scoped>
#headerTotal{

}

h1{
}
</style>
