<template>
  <div class="card">
    <img
      class="card__img"
      :src="require(`@/assets/books/${book.book_image.split('/')[3]}`)"
      :alt="book.title"
    />
    <div class="card__top_action">{{ book.rating }} out of 5</div>
    <div class="card__img-overlay">
      <div class="card__img-overlay__title">{{ book.title }}</div>
      <div class="card__img-overlay__subtitle">{{ book.author }}</div>
      <div class="card__img-overlay__caption">
        {{ book.publisher }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "BookCard",

  props: {
    book: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
.card {
  position: relative;
  display: flex;
  flex-direction: column;
  min-width: 0;
  width: 250px;
  word-wrap: break-word;
  background-clip: border-box;
  border-radius: 1rem;
  box-shadow: 0 6px 10px rgba(0, 0, 0, 0.08), 0 0 6px rgba(0, 0, 0, 0.05);
  transition: 0.3s transform cubic-bezier(0.155, 1.105, 0.295, 1.12),
    0.3s box-shadow,
    0.3s -webkit-transform cubic-bezier(0.155, 1.105, 0.295, 1.12);
  border: 5px solid transparent;
  overflow: hidden;

  &:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.12), 0 4px 8px rgba(0, 0, 0, 0.06);
    border-radius: 1rem;
  }

  &__img {
    display: block;
    width: 100%;
    object-fit: cover;
  }

  &__img-overlay {
    position: absolute;
    bottom: 0;
    left: 0;
    padding: 0.7rem;
    background-image: linear-gradient(45deg, black, transparent);
    width: 228px;

    &__title {
      font-size: 18px;
      font-weight: 500;
      font-stretch: normal;
      font-style: normal;
      line-height: 1.2;
      letter-spacing: -0.2px;
      color: #fff;
      max-width: 100%;
      margin: 0 0 7px;
      text-align: left;
    }

    &__subtitle {
      font-size: 13px;
      font-weight: 300;
      font-stretch: normal;
      font-style: normal;
      line-height: 1.4;
      letter-spacing: 0.4px;
      color: hsla(0, 0%, 100%, 0.9);
      text-align: left;
    }

    &__caption {
      font-size: 13px;
      font-weight: 300;
      font-stretch: normal;
      font-style: normal;
      line-height: 1.4;
      letter-spacing: 0.4px;
      color: hsla(0, 0%, 100%, 0.9);
      text-align: left;
    }
  }

  &__top_action {
    position: absolute;
    top: 0;
    right: 0;
    padding: 0.4rem;
    background: #003366;
    color: #fff;
    border-bottom-left-radius: 1rem;
    opacity: 0.9;
    font-size: 16px;
    font-weight: 400;
    font-stretch: normal;
    font-style: normal;
    line-height: normal;
    letter-spacing: 0.2px;
  }
}
</style>
