<template>
  <div class="container">
    <content-row>
      <h3 class="book-category">Hardcover Fiction</h3>

      <content-rail :items="books" class="content-rail--btn-offset-50">
        <template #item="{ item, itemIndex }">
          <div @click="getSelectedBook(itemIndex)">
            <BookCard
              :book="item"
              :style="
                itemIndex === itemIndexx
                  ? 'border: 5px solid #fff;'
                  : 'border: 5px solid transparent;'
              "
            />
          </div>
        </template>
      </content-rail>
    </content-row>
    <div class="content" v-if="!isEmpty(bookDetails)">
      <div class="content__left">
        <div class="content__left--title">{{ bookDetails.title }}</div>
        <img
          class="content__left--img"
          :src="
            require(`@/assets/books/${bookDetails.book_image.split('/')[3]}`)
          "
          :alt="bookDetails.title"
        />

        <div class="content__left--action">
          <button type="button" class="btn content__left--action--btn">
            Add to Favourites <span style="margin-left: 1rem">+</span>
          </button>
        </div>
      </div>
      <div class="content__right">
        <div class="content__right--title">{{ bookDetails.author }}</div>
        <div class="content__right--subtitle">{{ bookDetails.publisher }}</div>
        <p class="content__right--description">
          {{ bookDetails.description }}
        </p>
      </div>
      <div class="content__close" @click="closeDetails">
        <img :src="require('@/assets/close.png')" alt="close" />
      </div>
    </div>
  </div>
</template>

<script>
import isEmpty from "lodash/isEmpty";

export default {
  name: "Home",

  components: {
    ContentRow: () => import("@/components/ContentRow"),
    ContentRail: () => import("@/components/ContentRail/ContentRail.vue"),
    BookCard: () => import("@/components/BookCard.vue"),
  },

  data: () => ({
    books: [],
    bookDetails: {},
    itemIndexx: "",
  }),

  created() {
    const items = import("../data/books.json");
    items
      .then((item) => {
        this.books = item.results.books;
      })
      .catch((err) => console.log(err));
  },

  methods: {
    isEmpty,
    getSelectedBook(itemIndex) {
      this.itemIndexx = itemIndex;
      this.bookDetails = this.books[itemIndex];
    },

    closeDetails() {
      this.bookDetails = {};
      this.itemIndexx = "";
    },
  },
};
</script>

<style lang="scss" scoped>
.book-category {
  font-size: 22px;
  font-weight: 500;
  font-stretch: normal;
  font-style: normal;
  line-height: 1.27;
  letter-spacing: normal;
  color: #ffffff;
  margin-bottom: 1rem;
}

.content {
  display: flex;
  flex-direction: row;
  padding-top: 4rem;
  padding-left: 2rem;
  position: relative;

  &__close {
    position: absolute;
    top: 0;
    right: 0;
    padding-right: 1.5rem;
    padding-top: 3rem;
    cursor: pointer;
  }

  &__left {
    &--title {
      font-size: 40px;
      font-weight: 100;
      font-stretch: normal;
      font-style: normal;
      line-height: 1.2;
      letter-spacing: 0.6px;
      color: #c3a572;
      margin-bottom: 40px;
      margin-top: 0;
      max-width: 360px;
      text-align: left;
    }

    &--img {
      width: 60px;
      border-radius: 4px;
      object-fit: cover;
    }

    &--action {
      margin: 1rem 0;
      &--btn {
        color: #fff;
        background: #464646;
      }
    }
  }

  &__right {
    margin-left: 8rem;

    &--title {
      font-size: 18px;
      font-weight: 500;
      font-stretch: normal;
      font-style: normal;
      line-height: normal;
      letter-spacing: normal;
      color: #fff;
      margin-bottom: 2px;
    }

    &--subtitle {
      font-size: 14px;
      font-weight: 300;
      font-stretch: normal;
      font-style: normal;
      line-height: 1.44;
      letter-spacing: 0.43px;
      color: hsla(0, 0%, 100%, 0.6);
    }

    &--description {
      font-family: Helvetica Neue LT W05_45 Light;
      font-size: 14px;
      font-weight: 300;
      font-stretch: normal;
      font-style: normal;
      line-height: 1.36;
      letter-spacing: 0.4px;
      color: hsla(0, 0%, 100%, 0.7);
      word-break: break-word;
    }
  }
}
</style>
