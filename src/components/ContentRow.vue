<template functional>
  <section class="container container--w-full">
    <slot></slot>
  </section>
</template>

<style lang="scss" scoped>
.container {
  padding-left: 1.5rem;
  padding-right: 1.5rem;
  max-width: 100%;

  @media (min-width: 1024px) {
    padding-left: 1rem;
    padding-right: 1rem;
    max-width: 1024px;
  }

  @media (min-width: 1280px) {
    max-width: 1280px;
  }

  &--w-full {
    padding-left: 0px;
    padding-right: 0px;

    @media (min-width: 1280px) {
      max-width: 1280px;
    }

    @media (min-width: 1024px) {
      padding-left: 1rem;
      padding-right: 1rem;
    }
  }
}
</style>
