<template>
  <div>
    <h1>Test Page</h1>
    <foo />
    <bar />
  </div>
</template>

<script>
import foo from '~/components/foo'
import bar from '~/components/bar'

export default {
  components: {
    foo,
    bar,
  },
  created() {
    console.log('Test Page Created')
  },
}
</script>
