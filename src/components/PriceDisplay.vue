<template>
  <h2>Preise:</h2>
  <div class="price-container">
    <template v-for="(exchange, index) in exchanges" :key="index">
      <div>
        <h3 class="exchange-name">{{ exchange }}:</h3>

        <ul>
          <li>
            <span class="important">
              {{ Number.parseFloat(this.data[exchange]?.usd).toFixed(2) }}
              {{ getCurrencySymbol("usd") }}
            </span>
          </li>
          <li>
            <span class="important">
              {{ Number.parseFloat(this.data[exchange]?.eur).toFixed(2) }}
              {{ getCurrencySymbol("eur") }}
            </span>
          </li>
          <li>
            <span class="important">
              {{ Number.parseFloat(this.data[exchange]?.gbp).toFixed(2) }}
              {{ getCurrencySymbol("gbp") }}
            </span>
          </li>
          <li>
            <span class="important">
              {{ Number.parseFloat(this.data[exchange]?.jpy).toFixed(2) }}
              {{ getCurrencySymbol("jpy") }}
            </span>
          </li>
        </ul>
        <!-- 
        <ul>
          <template
            v-for="([currency, value], index) in Object.entries(
              this.data[exchange]
            )"
            :key="index"
          >
            <li>
              <span class="important"
                >{{ Number.parseFloat(value).toFixed(2) }}
                {{ getCurrencySymbol(currency) }}</span
              >
            </li>
          </template>
        </ul> -->

        <br />
      </div>
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
    getCurrencySymbol(currency) {
      if (currency === "usd") {
        return "$";
      } else if (currency === "eur") {
        return "€";
      } else if (currency === "gbp") {
        return "£";
      } else if (currency === "jpy") {
        return "¥";
      }
      return "";
    },
  },
};
</script>

<style>
@import "../assets/base.css";

.price-container {
  display: flex;
  justify-content: space-evenly;
}

.exchange-name {
  padding-bottom: 10px;
}

li {
  list-style-type: none;
}
ul {
  padding: 0;
  text-align: center;
}
</style>
