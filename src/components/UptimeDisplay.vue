<template>
  <h2>Laufzeit:</h2>
  <span class="important">{{ toTime() }}</span>
  <br /><br />
</template>

<script>
export default {
  props: {
    data: undefined,
  },
  methods: {
    toTime() {
      const days = Math.floor(this.data / (24 * 60 * 60));
      const hours = Math.floor(this.data / (60 * 60)) - days * 24;
      const minutes = Math.floor(this.data / 60) - days * 24 * 60 - hours * 60;
      const seconds =
        this.data - days * 24 * 60 * 60 - hours * 60 * 60 - minutes * 60;
      let result = "";
      if (days > 0) result += days + " Tage";
      if (hours > 0) {
        if (result !== "") result += ", ";
        result += hours + " Stunden";
        if (hours > 1) result += "s";
      }
      if (minutes > 0) {
        if (result !== "") result += ", ";
        result += minutes + " Minuten";
        if (minutes > 1) result += "s";
      }
      if (seconds > 0) {
        if (result !== "") result += ", ";
        result += seconds + " Sekunden";
        if (seconds > 1) result += "s";
      }
      return result;
      // return (
      //   days +
      //   "days, " +
      //   hours +
      //   " hours, " +
      //   minutes +
      //   "minutes, " +
      //   seconds +
      //   "seconds"
      // );
    },
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
