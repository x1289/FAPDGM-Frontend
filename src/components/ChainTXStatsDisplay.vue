<script>
export default {
  props: {
    data: undefined,
  },
};
</script>

<template>
  <h2>Statistiken der Blockchain-Transaktionen:</h2>
  <p v-if="data?.count !== undefined">
    Anzahl der Transaktionen in den letzten 30 Tagen:
    <span class="important">{{ data?.count }}</span>
  </p>
  <p v-if="data?.blockcount !== undefined">
    Anzahl der Blöcke in den letzten 30 Tagen:
    <span class="important">{{ data?.blockcount }}</span>
  </p>
  <p v-if="data?.txrate !== undefined">
    Transaktionsrate:
    <span class="important"
      >{{ Number.parseFloat(data?.txrate).toFixed(4) }} Transaktionen pro
      Sekunde</span
    >
  </p>
  <p v-if="data?.minutesperblock !== undefined">
    Blockzeit:
    <span class="important"
      >{{ Number.parseFloat(data?.minutesperblock).toFixed(4) }} Minuten pro
      Block</span
    >
  </p>
  <br />
</template>

<style>
@import "../assets/base.css";

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
  .important {
    font-weight: 800;
  }
}
</style>
