<template>
  <div class="container">
    <div>
      <h2>{{ headline }}</h2>
      <h3>{{ subhead }}</h3>
      <p>{{ cta }}</p>
      <button>Let's talk.</button>
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
