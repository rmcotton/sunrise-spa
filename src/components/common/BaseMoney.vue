<template>
  <span data-test="product-original-price">
    {{ formattedMoney }}
  </span>
</template>

<script>
export default {
  props: {
    money: Object,
  },

  computed: {
    formattedMoney() {
      return this.$n(this.amount, 'currency', this.$store.state.country);
    },

    amount() {
      if (this.money) {
        return this.money.centAmount / (10 ** this.money.fractionDigits);
      }
      return 0;
    },
  },
};
</script>
