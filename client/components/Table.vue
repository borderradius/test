<template>
  <table>
    <tbody>
      <tr v-for="item in data.rates" :key="item">
        <td>{{ item }}</td>
        <td>{{ item }}</td>
        <td>{{ item }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
      default: () => {
        return {}
      },
    },
  },
  watch: {
    data(newValue, oldValue) {
      console.log(newValue)
    },
  },
}
</script>

<style lang="scss" scoped></style>
