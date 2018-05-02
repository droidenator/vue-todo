<template>
  <div>
    <span>
      <input
        type="checkbox"
        value="on"
        v-model="item.isChecked"
      />
    </span>
    <span>{{ item.label }}</span>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    item: {
      type: Object,
      default: () => ({
        label: '',
        isChecked: false
      })
    }
  }
};
</script>
