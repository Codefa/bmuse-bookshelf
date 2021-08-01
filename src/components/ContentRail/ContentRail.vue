<template>
  <div :class="classes">
    <div ref="wrapper" class="content-rail__wrapper">
      <div ref="track" class="content-rail__track">
        <div
          v-for="(item, i) in items"
          :key="i"
          ref="items"
          class="content-rail__item"
        >
          <slot name="item" :item="item" :itemIndex="i"></slot>
        </div>
      </div>
    </div>
    <div class="content-rail__actions">
      <div
        @click="prev"
        aria-label="Previous"
        :class="{ hide_btn: !showPrev }"
        class="
          content-rail__btn content-rail__btn--left
          btn
          inline-flex
          btn-icon btn-md
        "
      >
        <img
          :src="require('@/assets/slider_arrow.png')"
          style="-webkit-transform: scaleX(-1); transform: scaleX(-1)"
          alt="slider_left_arrow"
          width="60"
          height="60"
        />
      </div>
      <div
        aria-label="Next"
        @click="next"
        :class="{ hide_btn: !showNext }"
        class="
          content-rail__btn content-rail__btn--right
          btn
          inline-flex
          btn-icon btn-md
        "
      >
        <img
          :src="require('@/assets/slider_arrow.png')"
          alt="slider_right_arrow"
          width="60"
          height="60"
        />
      </div>
    </div>
  </div>
</template>

<script>
import chunk from "lodash/chunk";
import debounce from "lodash/debounce";
const SCREEN_LG = 1024;
const SCREEN_RESIZE_REFRESH_RATE = 500;

export default {
  props: {
    items: {
      type: Array,
      required: true,
      default: () => [],
    },

    perPage: {
      type: Number,
      required: false,
      default: 4,
    },
  },

  data() {
    return {
      page: 1,
      itemWidth: 0,
    };
  },

  computed: {
    classes() {
      return `content-rail content-rail--${this.perPage}-col`;
    },
    showNext() {
      return this.page < this.pages;
    },
    showPrev() {
      return this.page > 1;
    },
    paginatedItems() {
      return chunk(this.items, this.perPage);
    },
    pages() {
      return this.paginatedItems.length;
    },
    hasMultiplePages() {
      return this.pages > 1;
    },
  },

  mounted() {
    this.recalculateOnResize = debounce(() => {
      if (window.innerWidth < SCREEN_LG) {
        this.clearTrackStyles();
        this.resetPagination();
      } else {
        this.resetScrollPosition();
        this.calculateOffset();
      }
    }, SCREEN_RESIZE_REFRESH_RATE);

    if (this.hasMultiplePages) {
      window.addEventListener("resize", this.recalculateOnResize);
    }
  },

  destroyed() {
    if (this.hasMultiplePages) {
      window.removeEventListener("resize", this.recalculateOnResize);
    }
  },

  methods: {
    next() {
      this.page += 1;
      this.calculateOffset();
    },

    prev() {
      this.page -= 1;
      this.calculateOffset();
    },

    calculateOffset() {
      let offset = 0;
      let items = 0;

      this.calculateTrackItemSize();

      if (this.page > 1) {
        for (let i = 1; i < this.page; i++) {
          items += this.paginatedItems[i].length;
        }

        offset = `-${items * this.itemWidth}`;
      }

      this.$refs.track.style.transform = `translate3d(${offset}px,0,0)`;
    },

    calculateTrackItemSize() {
      const item = this.$refs.items ? this.$refs.items[0] : null;

      if (item) {
        const styles = getComputedStyle(item);
        this.itemWidth = item.offsetWidth + parseInt(styles.marginRight);
      }
    },

    clearTrackStyles() {
      this.$refs.track.style.transform = "translate3d(0,0,0)";
    },

    resetScrollPosition() {
      this.$refs.wrapper.scrollLeft = 0;
    },

    resetPagination() {
      this.page = 1;
    },
  },
};
</script>

<style lang="scss">
@import "./ContentRail.scss";
</style>
