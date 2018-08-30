<template>
  <div class="action">
    <Button 
      @click.native="openModal"
      :text="text"
      :outline="true"
      type="primary"/>
    <Modal ref="modal">
      <Card :bordered="false" :rounded="true" :shadowed="true" width="400px">
        <template slot="card-header">
          <h3>Card Title</h3>
        </template>
        <template slot="card-content">
          <div 
            style="background: url('https://placeimg.com/800/200/any'); background-size: cover; background-position: center; width: 100%; height: 200px;" />
          <div style="padding: 15px; max-width: 600px;">
            <h3>Dynamic & Async Components</h3>
            <p>
              You’ll notice that if you select a post, switch to the Archive tab, 
              then switch back to Posts, it’s no longer showing the post you selected. 
              That’s because each time you switch to a new tab, Vue creates a new 
              instance of the currentTabComponent.
            </p>
          </div>
        </template>
        <template slot="card-footer">
          <Button text="Learn More" type="primary" :outline="true"/>
        </template>
      </Card>
    </Modal>
  </div>
</template>

<script>
import Button from '@/components/ui/Button.vue';
/**
 * Action button component
 */
export default {
  name: 'Action',
  props: {
    text: {
      type: String,
    },
  },
  methods: {
    /**
    * Gets called when the user clicks on the action button
    * @public
    */
    openModal() {
      this.$refs.modal.openModal();
    }
  },
  components: {
    Button,
  },
};
</script>

<style scoped lang="scss">
@import '@/styles/common.scss';
.action {
  
}
</style>

<docs>
```vue
    <div style="display: flex; align-items: center;">
      <Action text="Contact Us" />
    </div>
```
</docs>