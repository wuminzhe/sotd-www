<template>
  <div class="wrapper">
    <a v-if="item.website" :href="item.website" @click="$mixpanel.track('DApp - Website', { url: item.website })" class="link" target="_blank">Visit website<span v-if="item.isNsfw"> (NSFW)</span></a>
  </div>
</template>

<script>
  export default {
    computed: {
      item () {
        return this.$store.getters['dapp/active']
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import '~assets/css/settings';

  .link {
    position: relative;
    display: inline-block;
    margin: 10px 0;
    text-decoration: none;
    padding: 15px 25px;
    color: $color--gallery;
    background: $color--mine-shaft;
    box-shadow: 0 17px 70px rgba($color--mine-shaft,.4);
    @include tweakpoint('min-width', $tweakpoint--default) {
      padding: 20px 40px;
      font-size: 1.1rem;
    }
  }

  .wrapper {
    text-align: center;
  }
</style>
