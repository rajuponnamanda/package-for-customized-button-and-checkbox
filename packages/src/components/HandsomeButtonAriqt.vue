<template>
  <div>
    <button
      @click="onClick"
      @dblclick="onDoubleClick"
      :class="[
        'nice-handsome-button',
        'nice-handsome-button--' + color,
        'nice-handsome-button--' + size,
        {
          'nice-handsome-button--rounded': rounded,
          'nice-handsome-buttonariqt--default': !rounded
        }
      ]"
    >
      <slot>Handsome</slot>
    </button>
  </div>
</template>

<script lang="ts">
export default {
  props: {
    color: {
      type: String,
      default: 'blue',
      validator(x: string) {
        return ['blue', 'green', 'red'].indexOf(x) !== -1
      }
    },
    rounded: {
      type: Boolean,
      default: true
    },
    size: {
      type: String,
      default: 'default',
      validator(x: string) {
        return ['small', 'default', 'large'].indexOf(x) !== -1
      }
    }
  },

  methods: {
    onClick(event: any) {
      this.$emit('click', event)
    },

    onDoubleClick(event: any) {
      this.$emit('dblclick', event)
    }
  }
}
</script>

<style scoped>
.nice-handsome-button {
  display: inline-block;
  outline: 0;
  border: 1px solid rgba(0, 0, 0, 0.1);
  color: #ffffff;
  font-weight: 500;
  font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
  user-select: none;
  cursor: pointer;
}

/* --> COLORS <-- */

.nice-handsome-button--blue {
  background-color: #0194ef;
}

.nice-handsome-button--green {
  background-color: #1bb934;
}

.nice-handsome-button--red {
  background-color: #e1112c;
}

/* --> SIZES <-- */

.nice-handsome-button--small {
  padding: 8px 10px;
  font-size: 12px;
  line-height: 12px;
}

.nice-handsome-button--default {
  padding: 12px 14px;
  font-size: 14px;
  line-height: 16px;
}

.nice-handsome-button--large {
  padding: 16px 18px;
  font-size: 16px;
  line-height: 20px;
}

/* --> BOOLEANS <-- */

.nice-handsome-button--rounded {
  border-radius: 60px;
}
.nice-handsome-buttonariqt--default {
  border-radius: 0px;
}
</style>
