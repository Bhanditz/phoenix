<template>
  <v-text-field :label="label" append-icon="search"
    @input="onSearch" :value="searchQuery" autofocus="autofocus"></v-text-field>
</template>

<script>

export default {
  props: {
    value: {
      type: String,
      required: false,
      default: null
    },
    label: {
      type: String,
      required: false,
      default: ''
    },
    autofocus: {
      type: Boolean,
      required: false,
      default: false
    }
  },
  data: () => ({
    query: ''
  }),
  methods: {
    onSearch (query) {
      this.query = query
      this.$emit('search', query)
    }
  },
  computed: {
    searchQuery () {
      // please don't treat empty string the same as null...
      return (this.value === null) ? this.query : this.value
    }
  }
}
</script>

<style>

</style>
