<template>
  <div id="app">
    <div id="tela-1440px">
      <div id="logo">
        <img src="./assets/logo.png" alt="logo" />
      </div>

      <nav>
        <div id="tabs">
          <div class="divAtrasado">
            <router-link to="/late">Atrasadas</router-link>
          </div>
          <div class="divFazer">
            <router-link to="/todo">A Fazer</router-link>
          </div>
          <div class="divCompleto">
            <router-link to="/complete">Completas</router-link>
          </div>
        </div>
      </nav>

      <router-view />
    </div>
  </div>
</template>

<style >
#app {
  font-family: "Inter";
  text-align: center;
  color: #202d4180;
  display: flex;
  align-items: center;
  display: flex;
  justify-content: center;
}

#tela-1440px {
  width: 1440px;
  height: 812px;
}

#logo {
  height: 75px;
  position: relative;
  display: flex;
  padding-left: 20px;
  padding-top: 54px;
}
#logo img {
  width: 63px;
  height: 29.32px;
}

#tabs {
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 525px;
}
.divAtrasado {
  justify-content: start;
  height: 20px;
  width: 110px;
  padding-left: 20px;
}

.divFazer {
  height: 20px;
  width: 67px;
  padding-left: 22px;
}

.divCompleto {
  height: 20px;
  width: 72px;
  padding-left: 22px;
}

nav {
  
  padding-bottom: 0px;
}

nav a {
  color: #202d4180;
    text-decoration: none;
}

nav a.router-link-exact-active {
  color: #2563eb;
}
</style>
