<template>
  <div
    :class="classes"
    :style="{ width }"
    @click="toggleOptions">
    <div
      v-if="selectedOption"
      class="select-selected-option">
      <span>{{ selectedOption.text }}</span>
    </div>
    <div
      v-else
      class="select-placeholder-option">
      <span>Select an option</span>
    </div>
    <div class="select-indicator">
      <icon name="chevron-down"></icon>
    </div>
    <div 
      :class="{ ' open': open }"
      class="select-options">
      <Option
        v-for="(option, index) of options"
        :key="index"
        :text="option.text"
        :rounded="rounded"
        :selected="selectedOption === option"
        @click.native="() => selectOption(option)" />
    </div>
  </div>
</template>

<script>
import 'vue-awesome/icons';
import Icon from 'vue-awesome/components/Icon.vue';
import Option from '@/components/ui/Option.vue';
/**
 * Select component
 */
export default {
  name: 'Select',
  data() {
    return {
      selectedOption: null,
      open: false
    };
  },
  props: {
    options: {
      type: Array,
      required: true,
    },
    width: {
      type: String,
      default: '100%',
    },
    rounded: {
      type: Boolean,
    },
  },
  updated() {
    if (this.open) {
      document.body.addEventListener('click', this.closeOptions);
    } else {
      document.body.removeEventListener('click', this.closeOptions);
    }
  },
  computed: {
    classes() {
      let classes = 'select';
      classes += this.rounded ? ' rounded' : '';
      return classes;
    },
  },
  methods: {
    toggleOptions() {
      this.open = this.open ? this.open : !this.open ;
    },
    closeOptions(ev) {
      this.open = false;
    },
    selectOption(option) {
      this.selectedOption = option;
    }
  },
  components: {
    Icon,
  },
};
</script>

<style scoped lang="scss">
@import '@/styles/common.scss';
.select {
  position: relative;
  width: 100%;
  min-width: 200px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  border: 1px solid $alto;
  padding: 10px;
  cursor: pointer;
  transition: $transition;

  &:hover,
  &:focus {
    border: 1px solid $primary;
  }

  .select-options {
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    margin-top: 15px;
    background-color: $white;
    overflow: hidden;

    &.open {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      box-shadow: $shadow;
    }
  }

  .select-indicator {
    position: absolute;
    top: 50%;
    right: 10px;
    transform: translateY(-50%);
    width: 16px;
    height: 16px;
  }

  &.rounded {
    border-radius: $radius;

    .select-options {
      border-radius: $radius;
    }
  }
}
</style>

<docs>
```vue
    <template>
      <div style="display: flex; justify-content: space-evenly; align-items: center; background-color: #fff; padding: 15px;">
        <Select :options="options" width="200px" />
        <Select :options="options" width="200px" :rounded="true" />
      </div>
    </template>

    <script>
    export default {
      data() {
        return { 
          options: [
            {
              text: 'Jack',
              value: 'jack'
            },
            {
              text: 'Lucy',
              value: 'lucy'
            },
            {
              text: 'Tom',
              value: 'tom'
            },
          ]
        };
      }
    }
    </script>
```
</docs>