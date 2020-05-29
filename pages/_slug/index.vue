<template>
  <div class="page">
    <div class="content">
      <p class="headline">{{ headline }}</p>
      <p class="subhead">{{ subhead }}</p>
    </div>
    <div class="cta">
      <p>{{ cta }}</p>
      <div>
        <p>{{ "Let's talk.".toUpperCase() }} </p>
        <img src="arrow-right.svg" />
      </div>
    </div>
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
    headline() {
      return this.pageInfo ? this.pageInfo.blocks[0].headline : ''
    },
    subhead() {
      return this.pageInfo ? this.pageInfo.blocks[0].subhead : ''
    },
    cta() {
      return this.pageInfo ? this.pageInfo.blocks[0].cta : ''
    },
    background() {
      return this.pageInfo ? this.pageInfo.blocks[0].background : ''
    },
    title() {
      return this.pageInfo ? this.pageInfo.title : ''
    },
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
@import '~bukwild-stylus-library'
.page
  height: 100%
  display: flex
  flex-direction: column
.content
  height: 100%
  display: flex
  justify-content: space-between
  align-items: center
  fluid padding-top, 5, 1, 1440
  fluid margin-top, 100, 50, 1440
  fluid margin-bottom, 100, 50, 1440
  word-break: break-all
.headline
  fluid font-size, 84, 14, 1440
  line-height: 1
  margin: 0
  width: 50%
.subhead
  width: 50%
  fluid padding-left, 50, 25, 1440
  fluid padding-right, 50, 25, 1440
.cta
  display: flex
  align-items: center
  fluid min-height, 179, 150, 1440
  background-color: #ffffff
  fluid padding-left, 77, 50, 1440
  word-break: break-all
  p
    fluid font-size, 24, 12, 1440
    line-height: 1.33
    color: #000000
    width: 50%
  div
    display: flex
    justify-content: center
    width: 50%
    p
      fluid font-size, 11, 8, 1440
      font-weight: 500
      line-height: 1.82
      letter-spacing: 1px
      fluid width, 80, 60, 1440
</style>