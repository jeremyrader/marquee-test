<template>
  <div class="container">
    <div class="header">
      <div>
        <img src="images/abc_logo.svg" loading="lazy" alt="abc logo" />
        <div class="menu">
          <nuxt-link id="industries" to="/industries" class="link">Industries</nuxt-link>
          <nuxt-link to="/services" class="link">Services</nuxt-link>
          <nuxt-link to="/about-us" class="link">About Us</nuxt-link>
        </div>
      </div>
      <button class="contact-btn">Contact Us</button>
    </div>
    <nuxt />
  </div>
</template>

<script>

export default {
  mounted() {
    document.getElementById("industries").focus()
  }
}
</script>

<style lang="stylus">
@import '~bukwild-stylus-library'
body
  background-color: #222222
  color: white
  margin: 0
  fluid margin-left, 130, 30, 1440
  fluid margin-right, 130, 30, 1440
  fluid margin-top, 18.9, 5, 1440
  fluid font-size, 14, 8, 1440
  height: 100vh
  max-width: 1440px
  font-family: HelveticaNeue;
  fluid font-size, 14, 8, 1440
  font-weight: bold
  font-stretch: normal
  font-style: normal
  line-height: 1.86
  letter-spacing: normal
  color: #ffffff
  overflow-y: hidden

.menu
  display: flex
  flex-direction: column

.container
  height: 100%
  display: flex
  flex-direction: column

.header
  display: flex
  justify-content: space-between

.contact-btn
  fluid width, 139, 100, 1440
  fluid height, 42, 30, 1440
  border: solid 1px #ffffff
  fluid(font-size, 15, 10, 1440)
  color white
  background transparent
  text-align: center
  font-weight: 700

.contact-btn:hover
  cursor: pointer
  opacity: 0.8

.contact-btn:active
  opacity: 0.5

#__nuxt
  height: 100%

#__layout
  height: 100%

.link
  text-decoration none
  color inherit

.link:hover
  opacity: 0.8

.link:focus
  color #ffc004
  outline: none

@font-face {
  font-family: HelveticaNeue
  src: url(/fonts/HelveticaNeue-Bold.otf) format("opentype")
  font-weight: bold
  font-style: normal
  font-stretch: normal
}
</style>