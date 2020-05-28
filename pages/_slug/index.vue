<template>
  <div class="container">
    <div>
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
  </div>
</template>

<script>

export default {
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
.headline
  font-size: 84px
  line-height: 1
  letter-spacing: -2.2px
  margin: 0
.subhead
  padding-left: 171px
  padding-right: 171px
.content
  display: flex
  padding-top: 5px
.marquee
  display: flex
  align-items: center
  height: 179px
  background-color: #ffffff
  padding-left: 77px
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