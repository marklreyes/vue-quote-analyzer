<template>
	<td :class="coomputedClass">
		{{ priceList }}
	</td>
</template>
<script>
	export default {
  name: "QuoteCell",
  props: {
    priceList: {
      type: Array,
      required: true
    }
  },
  computed: {
    computedClass() {
      let className = 'default';

      // More complicated logic to determine what class should be applied

      return className;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.price-best {
		background-color: green;
		color: #fff;
	}

	.price-worst {
		background-color: red;
		color: #fff;
	}
</style>