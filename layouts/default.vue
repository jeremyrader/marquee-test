<template>
  <div>
    <div>
      <img src="abc_logo.svg" />
      <ul>
        <li><nuxt-link to="/industries">Industries</nuxt-link></li>
        <li><nuxt-link to="/services">Services</nuxt-link></li>
        <li><nuxt-link to="/about-us">About Us</nuxt-link> Us</li>
      </ul>
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

<style>
body {
  color: white;
}
</style>