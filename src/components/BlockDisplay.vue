<script>
export default {
  props: {
    data: undefined,
  },
};
</script>

<template>
  <h2>Aktueller Block:</h2>
  <p v-if="data?.confirmations !== undefined">
    Bestätigungen: <span class="important"> {{ data.confirmations }}</span>
  </p>
  <p v-if="data?.size !== undefined">
    Blockgröße:
    <span class="important">
      {{ Number.parseFloat(data.size / (1024 * 1024)).toFixed(3) }} MB
    </span>
  </p>
  <p v-if="data?.merkleroot !== undefined">
    Merkle-Wurzel:
    <span class="important"> "{{ data.merkleroot }}"</span>
  </p>
  <p v-if="data?.nonce !== undefined">
    Nonce:
    <span class="important"> {{ data.nonce }}</span>
  </p>
  <p v-if="data?.nTx !== undefined">
    Anzahl der Transaktionen:
    <span class="important"> {{ data.nTx }}</span>
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
}
</style>
