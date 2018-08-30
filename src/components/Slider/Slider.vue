<template>
  <div class="slider">
    <div
      v-for="(slide, index) of slides"
      :key="index"
      :class="slideClasses(slide)">
      <slot v-bind="slide"></slot>
    </div>
    <div
      @click="() => openSlide('previous')"
      class="slider-slide-control previous">
      <icon name="chevron-left" scale="2"></icon>
    </div>
    <div
      @click="() => openSlide('next')"
      class="slider-slide-control next">
      <icon name="chevron-right" scale="2"></icon>
    </div>
  </div>
</template>

<script>
import 'vue-awesome/icons';
import Icon from 'vue-awesome/components/Icon.vue';
/**
 * Slider component
 */
export default {
  name: 'Slider',
  data() {
    return {
      previousSlide: null,
      activeSlide: null,
      activeSlideIndex: null,
      nextSlide: null,
    };
  },
  props: {
    /**
     * List of slides
     */
    slides: {
      type: Array,
      required: true,
    },
  },
  methods: {
    /**
    * Calculate dynamic slide classes
    */
    slideClasses(slide) {
      let classes = 'slider-slide-container';
      classes += this.previousSlide === slide ? ' previous' : '';
      classes += this.activeSlide === slide ? ' active' : '';
      classes += this.nextSlide === slide ? ' next' : '';
      return classes;
    },
    /**
    * Opens the slide in given direction
    */
    openSlide(direction) {
      this.activeSlideIndex = this.getSlideIndex(direction);
      this.previousSlide = this.activeSlideIndex === 0 ? this.slides[this.slides.length - 1] : this.slides[this.activeSlideIndex - 1];
      this.activeSlide = this.slides[this.activeSlideIndex];
      this.nextSlide = this.activeSlideIndex === this.slides.length - 1 ? this.slides[0] : this.slides[this.activeSlideIndex + 1];
    },
    /**
    * Gets active slide index in given direction
    */
    getSlideIndex(direction) {
      if (direction === "next") {
        return this.activeSlideIndex === this.slides.length - 1 ? 0 : this.activeSlideIndex + 1;
      } else {
        return this.activeSlideIndex === 0 ? this.slides.length - 1 : this.activeSlideIndex - 1;
      }
    }
  },
  created() {
    this.previousSlide = this.slides[this.slides.length - 1];
    this.activeSlide = this.slides[0];
    this.activeSlideIndex = 0;
    this.nextSlide = this.slides[1];
  },
  components: {
    Icon,
  },
};
</script>

<style scoped lang="scss">
@import '@/styles/common.scss';
.slider {
  width: 100%;
  height: 800px;
  position: relative;
  overflow: hidden;

  .slider-slide-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 800px;
    display: none;
    transform: translateX(100%);
    transition: all 0.25s ease-in-out;

    &.active {
      display: flex;
      transform: translateX(0);
    }

    &.previous {
      display: flex;
      transform: translateX(-100%);
    }

    &.next {
      display: flex;
      transform: translateX(100%);
    }
  }

  .slider-slide-control {
    position: absolute;
    top: 50%;
    color: $white;
    
    &.previous {
      left: 25px;
      right: auto;
    }

    &.next {
      left: auto;
      right: 25px;
    }

    &:hover {
      cursor: pointer;
      color: $gallery;

      svg {
        filter: drop-shadow(1px 2px #000);
      }
    }
  }
}
</style>

<docs>
```vue
    <template>
      <div style="display: flex; align-items: center; background-color: #fff; padding: 15px;">
        <Slider :slides="slides">
          <template slot-scope="slide">
            <Slide :imageUrl="slide.image">
              <SlideContent :title="slide.title" :subtitle="slide.subtitle" />
            </Slide>
          </template>
        </Slider>
      </div>
    </template>

    <script>
    export default {
      data() {
        return { 
          slides: [
            {
              image: 'https://placeimg.com/1920/850/any',
              title: 'Some',
              subtitle: 'Title Here 1'
            },
            {
              image: 'https://placeimg.com/1920/850/any',
              title: 'Some',
              subtitle: 'Title Here 2'
            },
            {
              image: 'https://placeimg.com/1920/850/any',
              title: 'Some',
              subtitle: 'Title Here 3'
            },
            {
              image: 'https://placeimg.com/1920/850/any',
              title: 'Some',
              subtitle: 'Title Here 4'
            }
          ]
        };
      }
    }
    </script>
```
</docs>