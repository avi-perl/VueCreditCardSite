<template>
  <h3>You have {{ cardCount }} cards!</h3>
  <div class="cards">
    <CreditCard 
      v-for="card in cards" 
      :card="card"
      :key="card.id"
      :selected="card.id === selectedCardId"
      @selectCard="selectCard"
    />
  </div>
  <button @click="deleteCard" :disabled="selectedCardId === null">Delete Card</button>
  <!-- <AddCreditCard msg="Welcome to Your Vue.js App Avi" /> -->
</template>

<script>
// import AddCreditCard from "./components/AddCreditCard.vue";
import CreditCard from "./components/CreditCard.vue";

export default {
  name: "App",
  components: {
    // AddCreditCard,
    CreditCard,
  },
  data: function () {
    return {
      selectedCardId: null,
      cards: [
        {
          id: 1,
          name: "Avi Doe",
          number: "1111-2222-3333-4444",
          expiry: {
            month: "01",
            year: "18",
          },
          cvv: "352",
          selected: true,
          redacted: false,
        },
        {
          id: 2,
          name: "Jane Perl",
          number: "1111-2222-3333-4444",
          expiry: {
            month: "05",
            year: "17",
          },
          cvv: "352",
          selected: false,
          redacted: false,
        },
        {
          id: 3,
          name: "John Doe",
          number: "1111-2222-3333-4444",
          expiry: {
            month: "01",
            year: "18",
          },
          cvv: "352",
          selected: false,
          redacted: true,
        },
      ],
    };
  },
  computed: {
    cardCount: function () {
      return this.cards.length;
    },
  },
  methods: {
    selectCard: function (card) {
      console.log("Selected card " + card.id);
      this.selectedCardId = card.id;
    },
    deleteCard: function () {
      const cardToDelete = this.cards.find(
        (card) => card.id === this.selectedCardId
      );
      this.cards = this.cards.filter(card => card.id !== cardToDelete.id);
      this.selectedCardId = null;
    },
    addCard: function (cardData) {
      let newCard = {
        id: this.cardCount + 1,
        name: cardData.name || "",
        number: cardData.number || "",
        expiry: {},
        cvv: cardData.cvv || "",
        selected: false,
        redacted: false,
      }
      newCard.expiry.month = cardData.expirymonth || "";
      newCard.expiry.year = cardData.expiryyear || "";
      this.cards.push(newCard);
      this.selectCard(this.cardCount);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}

@font-face {
  font-family: OCRA;
  src: local("OCRA"),
    url("./assets/fonts/OCRA.ttf") format("truetype");
}

.cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
