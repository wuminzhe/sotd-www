<template>
  <ul class="list">
    <li class="item">Showing <strong @click="$mixpanel.track('DApps - Results count')">{{ itemsCount }}</strong> of <strong @click="$mixpanel.track('DApps - Results count')">{{ paginationTotalCount }}</strong> result{{ itemsCount == 1 ? '' : 's' }}</li>
  </ul>
</template>

<script>
  export default {
    computed: {
      itemsCount () {
        return this.$store.getters['dapps/itemsCount']
      },
      paginationTotalCount () {
        return this.$store.getters['dapps/paginationTotalCount']
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import '~assets/css/settings';

  .list {
    margin-top: 10px;
    @include tweakpoint('min-width', $tweakpoint--default) {
      margin-top: 0;
    }
  }
</style>
