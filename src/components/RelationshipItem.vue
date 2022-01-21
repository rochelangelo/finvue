<template>
  <div>
    <div class="cardItem gasto" v-if="type === 'gasto'">
      <h2>{{ reference }}</h2>
      <p>{{ category }}</p>
      <p>R${{ value }}</p>
    </div>
    <div class="cardItem receita" v-else>
      <h2>{{ reference }}</h2>
      <p>{{ category }}</p>
      <p>R${{ value }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "RelationshipItem",
  props: ["reference", "type", "category", "value"],
};
</script>

<style scoped>
.cardItem {
  border-radius: 5px;
  box-shadow: 7px 7px 13px 0px rgba(50, 50, 50, 0.22);
  padding: 30px;
  margin: 20px;
  width: 400px;
  transition: all 0.3s ease-out;
  border-left: 3px solid #446280;
}

.cardItem:hover {
  transform: translateY(-5px);
  cursor: pointer;
}

.gasto:hover {
  border-left: 3px solid #b84141;
}

.receita:hover {
  border-left: 3px solid #41b883;
}

.cardItem p {
  color: #6c6c6e;
  font-size: 16px;
}
</style>
