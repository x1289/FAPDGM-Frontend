<script>
import HelloWorld from "./components/HelloWorld.vue";
import BlockchainInfoDisplay from "./components/BlockchainInfoDisplay.vue";
import BlockDisplay from "./components/BlockDisplay.vue";
import ChainTXStatsDisplay from "./components/ChainTXStatsDisplay.vue";
import MempoolInfoDisplay from "./components/MempoolInfoDisplay.vue";
import UptimeDisplay from "./components/UptimeDisplay.vue";
import PriceDisplay from "./components/PriceDisplay.vue";

export default {
  components: {
    HelloWorld,
    BlockchainInfoDisplay,
    BlockDisplay,
    ChainTXStatsDisplay,
    MempoolInfoDisplay,
    UptimeDisplay,
    PriceDisplay,
  },
  data() {
    return {
      jsonData: undefined,
    };
  },
  mounted() {
    this.requestInterval = setInterval(() => {
      this.getJSONData();
    }, 1000);
  },
  methods: {
    async getJSONData() {
      fetch(
        `http://${import.meta.env.VITE_SERVER_URL}:${
          import.meta.env.VITE_SERVER_PORT
        }/`,
        {
          method: "GET",
          headers: {
            Accept: "application/json",
            "Content-Type": "application/json",
          },
        }
      )
        .then((response) => {
          return response.text();
        })
        .then((data) => {
          this.jsonData = JSON.parse(data);
          console.log(
            "request data from server successfull.",
            JSON.parse(data)
          );
        });
    },
  },
};
</script>

<template>
  <header>
    <div class="wrapper">
      <HelloWorld msg="Bitcoin Stats" />
    </div>
  </header>

  <main>
    <BlockchainInfoDisplay :data="jsonData?.blockchaininfo" />
    <BlockDisplay :data="jsonData?.block" />
    <ChainTXStatsDisplay :data="jsonData?.chaintxstats" />
    <MempoolInfoDisplay :data="jsonData?.mempoolinfo" />
    <UptimeDisplay :data="jsonData?.uptime" />
    <PriceDisplay :data="jsonData?.price" />
  </main>
</template>

<style>
@import "./assets/base.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }

  #app {
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 0 2rem;
  }

  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>
