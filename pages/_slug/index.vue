<template>
  <div class="page">
    <div class="content">
      <p class="headline">{{ headline }}</p>
      <p class="subhead">{{ subhead }}</p>
    </div>
    <div class="marquee">
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
.component
  height: 100%
.page
  height: 100%
  display: flex
  flex-direction: column
.headline
  font-size: 84px
  line-height: 1
  letter-spacing: -2.2px
  margin: 0
  width: 50%
.subhead
  width: 50%
  padding-left: 50px
  padding-right: 50px
.content
  height: 100%
  display: flex
  justify-content: space-between
  align-items: center
  padding-top: 5px
  margin-top: 100px
  margin-bottom: 100px
  word-break: break-all
.marquee
  display: flex
  align-items: center
  min-height: 179px
  background-color: #ffffff
  padding-left: 77px
  word-break: break-all
  p
    font-size: 24px
    line-height: 1.33
    letter-spacing: -0.63px
    color: #000000
    width: 50%
  div
    display: flex
    justify-content: center
    width: 50%
    p
      font-size: 11px
      font-weight: 500
      line-height: 1.82
      letter-spacing: 1px
      width: 80px
</style>