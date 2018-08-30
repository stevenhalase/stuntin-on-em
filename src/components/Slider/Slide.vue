<template>
  <div 
    class="slide" 
    :style="{ background: `url('${imageUrl}')` }">
    <slot class="slide-content"></slot>
  </div>
</template>

<script>
/**
 * Slide component
 */
export default {
  name: 'Slide',
  props: {
    /**
     * Image URL
     * `'https://placeimg.com/1920/850/any'`
     */
    imageUrl: {
      type: String,
    },
    backgroundColor: {
      type: String,
    },
  },
};
</script>

<style scoped lang="scss">
@import '@/styles/common.scss';
.slide {
  width: 100%;
  height: 800px;
  position: relative;

  .slide-content {
    position: absolute;
    top: 60%;
    left: 10%;
  }
}
</style>

<docs>
```vue
    <div style="display: flex; align-items: center; background-color: #fff; padding: 15px;">
      <Slide imageUrl="https://placeimg.com/1920/850/any">
        <SlideContent title="Your Move" subtitle="Is Our Priority" />
      </Slide>
    </div>
```
</docs>