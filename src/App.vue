<template>
  <div id="app">
    <header id="masthead">
      <div class="masthead-inner">
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
        <article class="masthead-text">
          <h2 class="masthead-text-headline">Bookshelf & Book Racks</h2>
          <p class="masthead-text-subheadline">
            Lorem Ipsum is simply dummy text of the printing and typesetting
            industry. Lorem Ipsum is simply dummy text of the printing and
            typesetting industry. Lorem Ipsum is simply dummy text of the
            printing and typesetting industry.
          </p>
        </article>
      </div>
    </header>
    <router-view />
  </div>
</template>

<style lang="scss">
body {
  font-family: Helvetica Neue LT W05_45 Light;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 0;
}

img {
  width: 100%;
}

#masthead {
  background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)),
    url(~@/assets/bg.jpg);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
  height: 100vh;
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
  // box-shadow: 0 1px 6px rgb(0 0 0 / 10%), 0 2px 24px rgb(0 0 0 / 20%);
}

.masthead-text {
  max-width: 30%;
  padding: 0 1rem;
  margin-top: 5rem;
}

.masthead-text-headline {
  font-size: 64px;
  font-weight: 100;
  font-stretch: normal;
  font-style: normal;
  line-height: 1.125;
  letter-spacing: normal;
  color: #fff;
  padding-left: 50px;
  margin: 0 0 16px;
}

.masthead-text-subheadline {
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
