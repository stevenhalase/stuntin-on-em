<template>
  <div :class="classes">
    <button
      v-if="circle"
      :disabled="disabled"
      :style="{ height, width }">
      <span v-if="text">{{ text }}</span>
      <icon v-if="icon" :name="icon"></icon>
    </button>
    <button
      v-else
      :disabled="disabled">
      <span v-if="text">{{ text }}</span>
      <icon v-if="icon" :name="icon"></icon>
    </button>
  </div>
</template>

<script>
import 'vue-awesome/icons';
import Icon from 'vue-awesome/components/Icon.vue';
/**
 * Button component with flexible options
 */
export default {
  name: 'Button',
  props: {
    /**
    * The text of the button
    * `'Hello World'`
    */
    text: {
      type: String,
    },
    /**
    * The icon of the button
    * `FA icon name: 'plus'`
    */
    icon: {
      type: String,
    },
    /**
    * The type of the button
    * `'primary', 'secondary', 'success', 'danger'`
    */
    type: {
      type: String,
    },
    /**
    * The size of the button
    * `'small', 'large'`
    */
    size: {
      type: String,
    },
    /**
    * Rounded button toggle
    * `true, false`
    */
    rounded: {
      type: Boolean,
    },
    /**
    * Circle button toggle
    * `true, false`
    */
    circle: {
      type: Boolean,
    },
    /**
    * Outline button toggle
    * `true, false`
    */
    outline: {
      type: Boolean,
    },
    /**
    * Optional button height for circle buttons
    * `'40px'`
    */
    height: {
      type: String,
      default: '40px',
    },
    /**
    * Optional button width for circle buttons
    * `'40px'`
    */
    width: {
      type: String,
      default: '40px',
    },
    /**
    * Disabled button toggle
    * `true, false`
    */
    disabled: {
      type: Boolean,
    },
  },
  computed: {
    classes() {
      let classes = 'button';
      classes += this.type ? ` ${this.type}` : '';
      classes += this.size ? ` ${this.size}` : '';
      classes += this.outline ? ' outline' : '';
      classes += this.rounded ? ' rounded' : '';
      classes += this.circle ? ' circle' : '';
      return classes;
    },
  },
  components: {
    Icon,
  },
};
</script>

<style scoped lang="scss">
@import '@/styles/common.scss';
.button {
  button {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: $button_standard_padding;
    margin: $button_standard_margin;
    font-size: $button_standard_fontsize;
    color: $button_primary_color;
    background-color: $button_primary_backgroundcolor;
    border: $button_standard_border;
    border-radius: $button_standard_borderradius;
    transition: $transition;

    &:hover {
      cursor: pointer;
      color: $button_primary_color_hover;
      background-color: $button_primary_backgroundcolor_hover;
    }

    &:disabled {
      opacity: 0.65;
      pointer-events: none;
    }

    span+svg {
      margin-left: 10px;
    }
  }

  &.small {
    button {
      padding: $button_small_padding;
      font-size: $button_small_fontsize;
    }
  }

  &.large {
    button {
      padding: $button_large_padding;
      font-size: $button_large_fontsize;
    }
  }

  &.primary {
    button {
      color: $button_primary_color;
      background-color: $button_primary_backgroundcolor;

      &:hover {
        color: $button_primary_color_hover;
        background-color: $button_primary_backgroundcolor_hover;
      }
    }

    &.outline {
      button {
        color: $button_primary_outline_color;
        border: 1px solid $button_primary_outline_bordercolor;
        background: transparent;

        &:hover {
          color: $button_primary_outline_color_hover;
          border: 1px solid $button_primary_outline_bordercolor_hover;
          background: transparent;
        }
      }
    }
  }

  &.secondary {
    button {
      color: $button_secondary_color;
      background-color: $button_secondary_backgroundcolor;

      &:hover {
        color: $button_secondary_color_hover;
        background-color: $button_secondary_backgroundcolor_hover;
      }
    }

    &.outline {
      button {
        color: $button_secondary_outline_color;
        border: 1px solid $button_secondary_outline_bordercolor;
        background: transparent;

        &:hover {
          color: $button_secondary_outline_color_hover;
          border: 1px solid $button_secondary_outline_bordercolor_hover;
          background: transparent;
        }
      }
    }
  }

  &.success {
    button {
      color: $button_success_color;
      background-color: $button_success_backgroundcolor;

      &:hover {
        color: $button_success_color_hover;
        background-color: $button_success_backgroundcolor_hover;
      }
    }

    &.outline {
      button {
        color: $button_success_outline_color;
        border: 1px solid $button_success_outline_bordercolor;
        background: transparent;

        &:hover {
          color: $button_success_outline_color_hover;
          border: 1px solid $button_success_outline_bordercolor_hover;
          background: transparent;
        }
      }
    }
  }

  &.danger {
    button {
      color: $button_danger_color;
      background-color: $button_danger_backgroundcolor;

      &:hover {
        color: $button_danger_color_hover;
        background-color: $button_danger_backgroundcolor_hover;
      }
    }

    &.outline {
      button {
        color: $button_danger_outline_color;
        border: 1px solid $button_danger_outline_bordercolor;
        background: transparent;

        &:hover {
          color: $button_danger_outline_color_hover;
          border: 1px solid $button_danger_outline_bordercolor_hover;
          background: transparent;
        }
      }
    }
  }

  &.rounded {
    button {
      border-radius: $button_rounded_borderradius;
    }
  }

  &.circle {
    button {
      border-radius: $button_circle_borderradius;
    }
  }
}
</style>

<docs>
Types
```vue
    <div style="display: flex; align-items: center;">
      <Button text="Primary" type="primary"/>
      <Button text="Secondary" type="secondary"/>
      <Button text="Success" type="success"/>
      <Button text="Danger" type="danger"/>
    </div>
```

Sizes
```vue
    <div style="display: flex; align-items: center;">
      <Button text="Small" type="primary" size="small"/>
      <Button text="Standard" type="primary"/>
      <Button text="Large" type="primary" size="large"/>
    </div>
```

Outline
```vue
    <div style="display: flex; align-items: center;">
      <Button text="Primary" type="primary" :outline="true"/>
      <Button text="Secondary" type="secondary" :outline="true"/>
      <Button text="Success" type="success" :outline="true"/>
      <Button text="Danger" type="danger" :outline="true"/>
    </div>
```

Rounded
```vue
    <div style="display: flex; align-items: center;">
      <Button text="Primary" type="primary" :rounded="true"/>
      <Button text="Secondary" type="primary" :rounded="true" :outline="true"/>
    </div>
```

Circle w/ Icon
```vue
    <div style="display: flex; align-items: center;">
      <Button type="primary" :circle="true" :icon="'search'"/>
      <Button type="primary" :circle="true" :outline="true" :icon="'search'"/>
    </div>
```

Disabled
```vue
    <div style="display: flex; align-items: center;">
      <Button text="Primary" type="primary" :disabled="true"/>
      <Button text="Secondary" type="secondary" :disabled="true"/>
      <Button text="Success" type="success" :disabled="true"/>
      <Button text="Danger" type="danger" :disabled="true"/>
    </div>
```
</docs>
