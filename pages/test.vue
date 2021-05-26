<template>
  <div class="page">
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
    console.log('Page Created')
  },
}
</script>
