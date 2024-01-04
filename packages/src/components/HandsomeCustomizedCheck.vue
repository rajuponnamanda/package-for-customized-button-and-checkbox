<template>
    <div>
      <!-- <button
        @click="onClick"
        @dblclick="onDoubleClick"
        :class="buttonClasses"
      >
        <slot>Handsome</slot>
      </button> -->
      <label class="checkbox-container">
    <input type="checkbox" :checked=checked @change="handleChange"  />
    <span class="checkmark" :class="['nice-handsome-checkbox--' + size, 'nice-handsome-checkbox--' + color]">
    </span>
    <slot></slot>
  </label>
      <!-- <input type="checkbox" @click="onClick"
      :class="checkBoxClasses"> -->
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, ref } from 'vue';
    
  let checked = true;
  
  export default defineComponent({
    props: {
      size: {
        type: String,
        default: 'default',
        validator(x: string) {
          return ['medium', 'default', 'large'].indexOf(x) !== -1;
        },
      }, 
      color: {
      type: String,
      default: 'blue',
      validator(x: string) {
        return ['blue', 'green', 'red', 'black'].indexOf(x) !== -1
      }
    },
    },
  
    setup(props, { emit }) {
      const onClick = (event: any) => {
        emit('click', event);
      };


    const handleChange = (event: any) => {
      checked = !checked;
      emit('update:modelValue', checked);
      emit('handleChange', event);
    };
  
      
  
      const checkBoxClasses = [
        'nice-handsome-checkBox',
        `nice-handsome-checkBox--${props.size}`,
      ];
  
      return {
        onClick,
        checked,
        handleChange,
        checkBoxClasses,
      };
    },
  });
  </script>
  
  <style scoped>
  .nice-handsome-checkBox {
    display: inline-block;
    outline: 0;
    border: 1px solid rgba(0, 0, 0, 0.1);
    color: #ffffff;
    font-weight: 500;
    font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
    user-select: none;
    cursor: pointer;
  }
  .checkbox-container {
 
  position: relative;
  /* padding-left: 28px; */
  
  cursor: pointer;
  font-size: 16px;
  user-select: none;
}

.checkbox-container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

.nice-handsome-checkbox--default {
  position: absolute;
  top: 0;
  left: 0;
  height: 30px;
  width: 30px;
  background-color: white;
  border: 2px solid #c20e0e;
  border-radius: 5px; /* Update the background-color to the desired color */
}

.nice-handsome-checkbox--medium {
  position: absolute;
  top: 0;
  left: 0;
  height: 40px;
  width: 40px;
  background-color: white;
  border: 2px solid #c20e0e;
  border-radius: 5px; /* Update the background-color to the desired color */
}

.nice-handsome-checkbox--red{
  border: 2px solid #c20e0e !important;
}

.nice-handsome-checkbox--green{
  border: 2px solid #0ec21d !important;
}

.nice-handsome-checkbox--blue{
  border: 2px solid hsl(202, 100%, 54%) !important;
}

.nice-handsome-checkbox--black{
  border: 2px solid #000000 !important;
}


.nice-handsome-checkbox--large {
  position: absolute;
  top: 0;
  left: 0;
  height: 50px;
  width: 50px;
  background-color: white;
  border: 2px solid #c20e0e;
  border-radius: 5px; /* Update the background-color to the desired color */
}

.checkbox-container:hover input ~ .checkmark {
  background-color: #fff;
}

.checkbox-container input:checked ~ .checkmark {
  background-color: white;
background-repeat: no-repeat;
background-size: cover;
 background-image: url('https://w7.pngwing.com/pngs/963/792/png-transparent-taurine-cattle-beef-cattle-computer-icons-cow-icon-cdr-white-face-thumbnail.png');
}

.checkmark:after {
  content: '';
  position: absolute;
  display: none;
}

.checkbox-container input:checked ~ .checkmark:after {
  display: block;
}

.checkbox-container .nice-handsome-checkbox--default:after {
  left: 2px;
  top: 2px;
  width: 12px;
  height: 12px;
}

  /* --> COLORS <-- */
  

  
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