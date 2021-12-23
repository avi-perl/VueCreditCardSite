<template>
  <CreditCardList :cards="cards" :card_count="cardCount" />
  <AddCreditCard msg="Welcome to Your Vue.js App Avi" />
</template>

<script>
import AddCreditCard from "./components/AddCreditCard.vue";
import CreditCardList from "./components/CreditCardList.vue";

export default {
  name: "App",
  components: {
    AddCreditCard,
    CreditCardList,
  },
  data: function () {
    return {
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
      this.cards.forEach(function (c) {
        c.selected = false;
      });
      this.cards[card.id - 1].selected = true;
      console.log(this.cards[card.id - 1]);
    },
    deleteCard: function (cardId) {
      this.cards = this.cards.filter(card => card.id !== cardId);
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
</style>
