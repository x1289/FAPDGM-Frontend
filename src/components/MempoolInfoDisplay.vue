<template>
  <h2>Memory Pool Info</h2>
  <p v-if="data?.size !== undefined">
    Anzahl der Transaktionen: <span class="important">{{ data.size }}</span>
  </p>
  <p v-if="data?.bytes !== undefined">
    Größe in Bytes: <span class="important">{{ data.bytes }}</span>
  </p>
  <p v-if="data?.minfee !== undefined">
    Minimale Gebühr: <span class="important">{{ data.minfee }}</span>
  </p>
  <p v-if="data?.totalfee !== undefined">
    Gebühren Gesamt: <span class="important">{{ data.totalfee }}</span>
  </p>
  <br />
</template>

<script>
export default {
  props: {
    data: undefined,
  },
};
</script>

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
