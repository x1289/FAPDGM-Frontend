<template>
  <header>
    <div class="wrapper">
      <h1 class="orange">Bitcoin Daten</h1>
      <div id="navigation">
        <a href="#/">
          <i class="bi bi-house-fill fs-5"></i>
          <span>Home</span>
        </a>
        <a href="#/api-doc">
          <i class="bi-book fs-5"></i>
          <span>API Doc</span>
        </a>
      </div>
    </div>
  </header>

  <main>
    <component :is="currentView" />
  </main>
</template>

<script>
import MainPage from "./pages/MainPage.vue";
import APIDoc from "./pages/APIDoc.vue";

const routes = {
  "/": MainPage,
  "/api-doc": APIDoc,
};

export default {
  data() {
    return {
      currentPath: window.location.hash,
    };
  },
  computed: {
    currentView() {
      return routes[this.currentPath.slice(1) || "/"] || "MainPage";
    },
  },
  mounted() {
    window.addEventListener("hashchange", () => {
      this.currentPath = window.location.hash;
    });
    this.getJSONData();
    this.requestInterval = setInterval(() => {
      this.getJSONData();
    }, 3000);
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
        });
    },
  },
};
</script>

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
.orange {
  text-decoration: none;
  color: #f7931a;
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
    flex-direction: column;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}

#navigation a {
  padding: 5px 15px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

#navigation a i {
  padding-right: 10px;
}

.btn-primary {
  background-color: #f7931a;
  border-color: #f7931a;
}
</style>
