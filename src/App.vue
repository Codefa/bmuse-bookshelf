<template>
  <div id="app">
    <div class="main-background">
      <nav class="main-nav">
        <div class="site-logo">
          <img :src="require('@/assets/bmuse_logo.png')" alt="logo" />
        </div>
        <ul class="top-nav">
          <li class="top-nav-link">
            <img class="search-icon" :src="require('@/assets/search.png')" />
          </li>
        </ul>
      </nav>

      <section class="section-showcase">
        <div class="container">
          <div>
            <h1 class="headline">Bookshelf & Book Racks</h1>
            <p class="subheadline">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Quo
              repudiandae rerum libero ipsum asperiores omnis mollitia, nostrum
              commodi placeat ea itaque modi corrupti corporis nam voluptas aut
              reprehenderit eaque culpa.
            </p>
          </div>
        </div>
      </section>
    </div>
    <router-view />
  </div>
</template>

<style lang="scss">
html {
  background-color: #141517;
}

body {
  font-family: Helvetica Neue LT W05_45 Light;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 0;
}

img {
  width: 100%;
}

.main-background {
  background: url(~@/assets/bg.jpg) no-repeat top / cover;
  height: 60vh;
  max-height: 700px;
  min-height: 300px;
}

.container {
  margin: auto;
  overflow: hidden;
  padding: 0 2rem;
}

/* showcase section */

.section-showcase {
  margin: 2rem 0;
}

.section-showcase .container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: center;
  justify-content: center;
}

.main-nav {
  padding: 0.5rem 2.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  box-sizing: border-box;
}

.site-logo {
  margin: 0;
}

.site-logo img {
  height: 40px;
  width: auto;
}

.top-nav {
  list-style: none;
  padding: 1rem 0;
  margin: 0;
  display: flex;
  justify-content: space-between;
}

.search-icon {
  width: 17px;
  height: 17px;
  background: #333;
  padding: 12px;
  border-radius: 100%;
}

.headline {
  font-size: 64px;
  font-weight: 100;
  font-stretch: normal;
  font-style: normal;
  line-height: 1.125;
  letter-spacing: normal;
  color: #fff;
  padding-left: 50px;
  margin: 0 60px 10px 0;
}

.subheadline {
  font-size: 16px;
  font-weight: 300;
  font-stretch: normal;
  font-style: normal;
  line-height: 1.38;
  letter-spacing: 0.4px;
  color: #fff;
  margin: 0;
  max-width: 460px;
  padding-left: 50px;
}
</style>
