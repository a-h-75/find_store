<template>
<div>

</div>
</template>

<script>

export default {
  methods() {
    asyncProcess().then((res) => {
      console.log(res)
    }).catch((err) => {
      console.log(err)
    })
  },
  mounted() {
    const asyncProcess = () => {
      setTimeout(() => {
        resolve('Hello')
      }, 3000)
    }

  }
}

</script>

<style>

</style>
