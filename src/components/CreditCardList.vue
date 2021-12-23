<template>
  <h3>You have {{ card_count }} cards!</h3>
  <div class="cards">
    <CreditCard 
      v-for="card in cards" 
      v-bind:card="card"
      v-bind:key="card.id"
    />
  </div>
</template>

<script>
import CreditCard from "./CreditCard.vue";

export default {
  name: "CreditCardList",
  components: {
    CreditCard,
  },
  props: {
    cards: Array,
    card_count: Number,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
