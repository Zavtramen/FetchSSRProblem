<template>
  <div class="foo">
    Foo {{ state }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      state: 'loading',
    }
  },
  async fetch() {
    console.log('Foo Fetch Start')
    this.state = await new Promise((resolve, reject) => {
      setTimeout(resolve, 500, 'fetched')
    })
    console.log('Foo Fetch End')
  },
  created() {
    console.log('Foo Created')
  },
}
</script>
