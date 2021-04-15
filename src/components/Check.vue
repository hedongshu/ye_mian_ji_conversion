<template>
  <div>
    <input
      type="radio"
      :name="span"
      :id="span"
      :value="value"
      v-model="_modelValue"
    >
    <label :for="span">{{span}}</label>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  props: {
    span: {
      type: String,
      required: true,
    },
    value: {
      type: [Number, String],
      required: true,
    },
    modelValue: [Number, String],
  },

  setup(props) {
    console.log(props);
  },

  computed: {
    _modelValue: {
      get(): string | number {
        return this.modelValue as string | number;
      },
      set(value: string | number): void {
        this.$emit("update:modelValue", value);
      },
    },
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
