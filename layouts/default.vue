<template>
  <div class="container">
    <div class="header">
      <div>
        <img src="abc_logo.svg" />
        <div style="display: flex; flex-direction: column">
          <nuxt-link to="/industries" class="link">Industries</nuxt-link>
          <nuxt-link to="/services" class="link">Services</nuxt-link>
          <nuxt-link to="/about-us" class="link">About Us</nuxt-link>
        </div>
      </div>
      <button class="contact Text-Style">Contact Us</button>
    </div>
    <nuxt />
  </div>
</template>

<script>

export default {}
</script>

<style lang="stylus">
body
  color: white
  margin: 0px
  margin-left: 130px
  margin-right: 130px
  margin-top: 18.9px
  font-size: 14px
  height: 100vh
  max-width: 1440px
  font-family: HelveticaNeue;
  font-size: 14px;
  font-weight: bold;
  font-stretch: normal;
  font-style: normal;
  line-height: 1.86;
  letter-spacing: normal;
  color: #ffffff;

#__nuxt
  height: 100%

#__layout
  height: 100%

.container
  height: 100%
  display: flex
  flex-direction: column

.link
  text-decoration none
  color inherit

.link:focus
  color #ffc004

.header
  display: flex
  justify-content: space-between

.contact
  width: 139px
  height: 42px
  border: solid 1px #ffffff
  font-size: 15px
  color white
  background transparent

@font-face {
  font-family: HelveticaNeue;
  src: local(HelveticaNeue-Bold),
    url(/fonts/HelveticaNeueBold.ttf) format("truetype")
  font-weight: bold;
  font-style: normal;
  font-stretch: normal;
}
.Text-Style {
  font-family: HelveticaNeue;
  font-size: 14px;
  font-weight: bold;
  font-stretch: normal;
  font-style: normal;
  line-height: 1.86;
  letter-spacing: normal;
  color: #ffffff;
}

</style>