<template>
  <section>
    <h1>{{ pageTitle }}</h1>

    <ul>
      <li v-for="user of users" :key="user.id">
        <a href="#" @click.prevent="goTo(user)" >{{ user.name }} ({{user.email}})</a>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  async asyncData({store}) {
    try {
      const users = await store.dispatch('users/fetchUsers');
      return {users};
    } catch (e) {
      error(e);
    }
  },
  data: () => ({
    pageTitle: 'Users Page',
  }),
  methods: {
    goTo(user) {
      this.$router.push('/users/' + user.id);
    }
  }
}
</script>

<style scoped>

</style>
