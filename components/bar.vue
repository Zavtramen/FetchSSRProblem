<template>
  <div>
    Bar {{ state }}
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
    console.log('Bar Fetch Start')
    this.state = await new Promise((resolve, reject) => {
      setTimeout(resolve, 100, 'fetched')
    })
    console.log('Bar Fetch End')
  },
  created() {
    console.log('Bar Created')
  },
}
</script>
