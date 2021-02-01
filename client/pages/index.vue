<template>
  <div class="container">
    <Select
      v-model="base"
      :option-data="getCountryLists"
      default-value=""
      default-name="나라를 선택해주세요."
      option-name-key="country"
      option-value-key="value"
    />
    <Table :data="{ base, date, rates }" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      base: '',
      date: '',
      rates: {},
    }
  },
  computed: {
    getCountryLists() {
      const listsTemp = Object.entries(this.rates)
      const lists = []
      for (const item of listsTemp) {
        lists.push({ country: item[0], value: item[0] })
      }
      return lists
    },
  },
  async created() {
    await this.getLists('latest')
  },
  methods: {
    async getLists(segment = '') {
      try {
        const { base, date, rates } = await this.$axios.$get(segment)
        this.base = base
        this.date = date
        this.rates = rates
      } catch (e) {
        console.error(e)
      }
    },
  },
}
</script>
