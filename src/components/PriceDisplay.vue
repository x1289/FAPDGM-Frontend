<template>
  <h2>price</h2>
  <div>
    <template v-for="(exchange, index) in exchanges" :key="index">
      {{ exchange }}
      <br />
      <ul>
        <template
          v-for="([currency, value], index) in Object.entries(
            this.data[exchange]
          )"
          :key="index"
        >
          <li>{{ currency.toUpperCase() }}: {{ value }}</li>
        </template>
      </ul>

      <br />
    </template>
  </div>
  <br /><br />
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  computed: {
    exchanges() {
      return Object.keys(this.data);
    },
  },
  methods: {
    exchangeData(exchange) {
      return this.data[exchange];
    },
  },
};
</script>

<style>
@import "../assets/base.css";

li {
  list-style-type: none;
}
</style>
