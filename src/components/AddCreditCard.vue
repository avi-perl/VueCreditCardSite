<template>
  <form @submit.prevent="submit" class="col-50">
    <h3>Payment</h3>
    <br />
    <label for="fname">Accepted Cards</label>
    <div class="icon-container">
      <i class="fa fa-cc-visa" style="color: navy"></i>
      <i class="fa fa-cc-amex" style="color: blue"></i>
      <i class="fa fa-cc-mastercard" style="color: red"></i>
      <i class="fa fa-cc-discover" style="color: orange"></i>
    </div>
    <label for="cname">Name on Card</label>
    <input type="text" id="cname" name="cardname" placeholder="John More Doe" v-model="name"/>
    <label for="ccnum">Credit card number</label>
    <input
      type="text"
      id="ccnum"
      name="cardnumber"
      placeholder="1111-2222-3333-4444"
      v-model="number"
    />
    <label for="expmonth">Exp Month</label>
    <input type="text" id="expmonth" name="expmonth" placeholder="September" v-model="expirymonth"/>
    <div class="row">
      <div class="col-50">
        <label for="expyear">Exp Year</label>
        <input type="text" id="expyear" name="expyear" placeholder="2018" v-model="expiryyear"/>
      </div>
      <div class="col-50">
        <label for="cvv">CVV</label>
        <input type="text" id="cvv" name="cvv" placeholder="352" v-model="cvv"/>
      </div>
    </div>
    <button type="submit">SUBMIT</button>
  </form>
</template>

<script>
export default {
  name: "AddCreditCard",
  props: {
    msg: String,
    items: Array,
  },
  methods: {
    submit: function () {
      console.log(this.number);
      this.$root.addCard(this);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
