<script>
export default {
  props: {
    data: undefined,
  },
};
</script>

<template>
  <h2>Blockchain Daten:</h2>

  <p v-if="data?.blocks !== undefined">
    Anzahl der Blöcke insgesamt:
    <span class="important">{{ data.blocks }} Blöcke</span>
  </p>
  <p v-if="data?.difficulty !== undefined">
    Schwierigkeit:
    <span class="important">{{ data.difficulty }}</span>
  </p>
  <p v-if="data?.verificationprogress !== undefined">
    Syncronisationsstatus:
    <span class="important">
      {{ Number.parseFloat(data.verificationprogress).toFixed(10) * 100 }} %
    </span>
  </p>
  <p v-if="data?.sizeondisk !== undefined">
    Speicherbedarf:
    <span class="important">
      {{
        (Number.parseFloat(data.sizeondisk) / (1024 * 1024 * 1024)).toFixed(3)
      }}
      GB
    </span>
  </p>
  <p v-if="data?.bestblockhash !== undefined">
    Aktueller Blockhash:
    <span class="important"> "{{ data.bestblockhash }}" </span>
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
