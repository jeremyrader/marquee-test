<template>
  <div class="container">
    <div>
      <h2>
        Lorem ipsum dolor sit amet
      </h2>
      <h3>Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</h3>
      <p>Nemo enim ipsam voluptatem quia voluptas.</p>
      <button>Let's talk.</button>
    </div>
  </div>
</template>

<script>

export default {
  mounted() {
    fetch('/content.json')
      .then(res => res.json())
      .then(data => console.log(data))
  }
}
</script>