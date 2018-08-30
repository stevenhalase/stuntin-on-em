<template>
  <div class="slide-content">
    <h2 class="slide-content-title">{{ title.toUpperCase() }}</h2>
    <h2 class="slide-content-subtitle">{{ subtitle.toUpperCase() }}</h2>
  </div>
</template>

<script>
/**
 * SlideContent component
 */
export default {
  name: 'SlideContent',
  props: {
    /**
    * Slide title
    * `'Your Move'`
    */
    title: {
      type: String,
      required: true,
    },
    /**
    * Slide subtitle
    * `'Is Out Priority'`
    */
    subtitle: {
      type: String,
      required: true,
    },
  }
};
</script>

<style scoped lang="scss">
@import '@/styles/common.scss';
.slide-content {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;

  .slide-content-title {
    font-size: 28px;
    color: $white;
    background-color: $primary;
    padding: 25px;
    width: fit-content;
  }

  .slide-content-subtitle {
    font-size: 28px;
    color: $mineshaft;
    background-color: $buttercup;
    padding: 25px;
    width: fit-content;
  }
  
}
</style>

<docs>
```vue
    <div style="display: flex; align-items: center; background-color: #fff; padding: 15px;">
      <SlideContent title="Your Move" subtitle="Is Our Priority" />
    </div>
```
</docs>