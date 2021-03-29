<template>
  <section>
    <h1>{{ user.name }}</h1>
  </section>
</template>

<script>
export default {
  validate({params}) {
    return /^\d+$/.test(params.id);
  },
  asyncData({params, error}){
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        // reject(error(new Error('User Not Found')));
        resolve( {
          user: {
            name: `Test user ${params.id}`
          }
        })
      }, 1500);
    })
  }
}
</script>

<style scoped>

</style>
