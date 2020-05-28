<template>
  <div>
    <div style="display: flex; justify-content: space-between;">
      <div>
        <img src="abc_logo.svg" />
        <div style="display: flex; flex-direction: column">
          <nuxt-link to="/industries">Industries</nuxt-link>
          <nuxt-link to="/services">Services</nuxt-link>
          <nuxt-link to="/about-us">About Us</nuxt-link>
        </div>
      </div>
      <button>Contact Us</button>
    </div>
    <nuxt />
  </div>
</template>

<script>

export default {
  head() {
    return {
      title: this.title,
      bodyAttrs: {
        style: `background-image: url(/backgrounds/${this.background})`
      }
    }
  },
  data() {
    return {
      pageInfo: null
    }
  },
  computed: {
    title() {
      return this.pageInfo ? this.pageInfo.title : ''
    },
    background() {
      return this.pageInfo ? this.pageInfo.blocks[0].background : ''
    }
  },
  mounted() {
    fetch('/content.json')
      .then(res => res.json())
      .then(data => {
        this.pageInfo = data['pages'].find(page => page.slug === this.$route.params.slug)
      })
  }
}
</script>

<style lang="stylus">
body
  color: white
  margin-left: 130px
  margin-right: 130px
  margin-top: 18.9px
  font-size: 14px

</style>