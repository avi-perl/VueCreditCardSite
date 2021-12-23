<template>
  <div
    class="card"
    :class="{ 'selected-card': card.selected, 'redacted-card': card.redacted }"
    v-on:click="this.$root.selectCard(card)"
  >
    <div v-if="!card.redacted" class="bank-name" title="BestBank">BestBank</div>
    <div v-else class="bank-name" title="Redacted">Redacted</div>
    <template v-if="!card.redacted">
      <div class="chip">
        <div class="side left"></div>
        <div class="side right"></div>
        <div class="vertical top"></div>
        <div class="vertical bottom"></div>
      </div>
      <div class="data">
        <div class="pan" :title="card.number">{{ card.number }}</div>
        <div class="first-digits">{{ card.number.split("-")[0] }}</div>
        <div class="exp-date-wrapper">
          <div class="left-label">EXPIRES END</div>
          <div class="exp-date">
            <div class="upper-labels">MONTH/YEAR</div>
            <div
              class="date"
              :title="card.expiry.month + '/' + card.expiry.year"
            >
              {{ card.expiry.month }}/{{ card.expiry.year }}
            </div>
          </div>
        </div>
        <div class="name-on-card" :title="card.name">{{ card.name }}</div>
      </div>
      <div class="lines-down"></div>
      <div class="lines-up"></div>
    </template>
    <button v-on:click="this.$root.deleteCard(card.id)">deleteCard {{ card.id }}</button>
  </div>
</template>

<script>
export default {
  name: "CreditCard",
  props: {
    card: Object,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card {
  /* position: absolute; */
  margin: 10px;
  width: 85.6mm;
  height: 53.98mm;
  color: #fff;
  /* font: 22px/1; */
  background: rgb(52, 17, 80);
  border: 1px solid black;
  border-radius: 10px;
  overflow: hidden;
  padding: 15px;
}

.redacted-card {
  border: rgb(54, 54, 54);
  background: #ccc;
}

.selected-card {
  border: 3px solid red;
}

.bank-name {
  float: right;
  margin-top: 15px;
  margin-right: 30px;
  font: 800 28px sansSerif;
}

.pan,
.month,
.year,
.year:before,
.name-on-card,
.date {
  position: relative;
  z-index: 20;
  letter-spacing: 1px;
  text-shadow: 1px 1px 1px #000;
}
.pan {
  position: relative;
  z-index: 50;
  margin: 0;
  letter-spacing: 1px;
  font-size: 26px;
}

.first-digits {
  margin: 0;
  font: 400 10px/1 sansSerif;
}
.exp-date-wrapper {
  margin-top: 5px;
  margin-left: 64px;
  line-height: 1;
}
.left-label {
  float: left;
  display: inline-block;
  width: 40px;
  font: 400 7px/8px sansSerif;
  letter-spacing: 0.5px;
}
.exp-date {
  display: inline-block;
  float: left;
  margin-top: -10px;
  margin-left: 10px;
  text-align: center;
}

.name-on-card {
  margin-top: 10px;
}
</style>
