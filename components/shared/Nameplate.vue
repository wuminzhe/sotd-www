<template>
  <ul class="list">
    <li class="item -logo"><nuxt-link @click.native="$mixpanel.track('Nav - Home')" to="/" class="link -logo"><img src="/images/logo.png" width="172" alt="State of the ÐApps" class="image"></nuxt-link></li>
    <li class="item -description">A Curated Collection of <strong>{{ dappCount }}</strong> Decentralized Apps <br>for <strong class="company-name">ethereum</strong></li>
  </ul>
</template>

<script>
  export default {
    computed: {
      dappCount () {
        return this.$store.getters['dappCount']
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import '~assets/css/settings';

  .company-name {
    letter-spacing: .2rem;
  }

  .image {
    display: block;
    margin: 0 auto;
  }

  .item {
    @include tweakpoint('min-width', $tweakpoint--default) {
      margin-right: 10px;
    }
    &.-logo, &.-description {
      margin-bottom: 5px;
      @include tweakpoint('min-width', $tweakpoint--default) {
        margin-bottom: 0;
      }
    }
  }

  .list {
    text-align: center;
    margin-top: 20px;
    line-height: 1.4;
    @include tweakpoint('min-width', $tweakpoint--default) {
      margin-top: 0;
      text-align: left;
      display: flex;
      align-items: center;
      line-height: 1.2;
    }
  }
</style>
