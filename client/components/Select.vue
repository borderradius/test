<template>
  <div class="relative">
    <select ref="select" :value="value" :disabled="disabled" @change="onChange">
      <option :value="defaultValue">{{ defaultName }}</option>
      <option
        v-for="(op, index) in optionData"
        :key="index"
        :value="op[optionValueKey]"
      >
        {{ op[optionNameKey] }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    defaultName: {
      type: String,
      default: '',
    },
    defaultValue: {
      type: [String, Number],
      default: '',
    },
    optionData: {
      type: Array,
      default: () => {
        return []
      },
    },
    optionNameKey: {
      type: String,
      default: '',
    },
    optionValueKey: {
      type: String,
      default: '',
    },
    value: {
      type: [String, Number],
      default: '',
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    onChange() {
      this.$emit('input', this.$refs.select.value)
    },
  },
}
</script>
