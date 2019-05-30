<template>
    <div>
        {{ label }}<input
            :type="type"
            :name="name"
            :placeholder="placeholder"
            :value="value"
            @input="updateValue"
            @focus="$emit('focus', $event)"
            @blur="$emit('blur', $event)"
        >
    </div>
</template>
<script>
export default {
    props: {
      value: {},
      label: { type: String },
      name: { type: String, require: true },
      type: { type: String, default: 'text' },
      placeholder: { type: String }
    },
    methods: {
      updateValue (e) {
        this.$emit('input', e.target.value)
      }
    }
}
</script>