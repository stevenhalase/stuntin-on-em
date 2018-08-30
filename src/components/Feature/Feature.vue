<template>
  <div class="feature">
    <Card :bordered="false">
      <template slot="card-content">
        <div 
          style="background: url('https://placeimg.com/800/200/any'); background-size: cover; background-position: center; width: 100%; height: 200px;" />
        <div class="feature-content" style="padding: 15px; max-width: 600px;">
          <Button 
            text="Read More" 
            type="primary" 
            size="small" 
            icon="chevron-right"
            class="feature-read-more"/>
          <OverLine>
            <h3>Dynamic & Async Components</h3>
          </OverLine>
          <p>
            You’ll notice that if you select a post, switch to the Archive tab, 
            then switch back to Posts, it’s no longer showing the post you selected. 
            That’s because each time you switch to a new tab, Vue creates a new 
            instance of the currentTabComponent.
          </p>
        </div>
      </template>
    </Card>
  </div>
</template>

<script>
import Card from '@/components/Card/Card.vue';
import OverLine from '@/components/OverLine/OverLine.vue';
/**
 * Feature component
 */
export default {
  name: 'Feature',
  components: {
    Card,
    OverLine,
  },
};
</script>

<style scoped lang="scss">
@import '@/styles/common.scss';
.feature {

  .feature-content {
    position: relative;
    
    .feature-read-more {
      position: absolute;
      right: 0;
      top: -40px;
    }
  }
}
</style>

<docs>
```vue
    <div style="display: flex; align-items: center; background-color: #2C3741; padding: 15px;">
      <Feature />
    </div>
```
</docs>