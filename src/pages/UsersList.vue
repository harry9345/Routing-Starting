<template>
  <div>
    <button @click="ConfirmInput">Confirm mine</button>
    <ul>
      <user-item v-for="user in users" :key="user.id" :name="user.fullName" :role="user.role"></user-item>
    </ul>
    <button @click="savedChanges">Save new changes</button>
  </div>
</template>

<script>
import UserItem from '../components/users/UserItem.vue';

export default {
  components: {
    UserItem
  },
  data() {
    return {
      changeSaved: false
    };
  },
  inject: ['users'],
  methods: {
    ConfirmInput() {
      // changintg to teams
      this.$router.push('/teams');
    },
    savedChanges() {
      this.changeSaved = true;
    }
  },
  beforeRouteEnter(to, from, next) {
    console.log('enterlist users here');
    console.log(to, from);
    next();
  },
  beforeRouteLeave(to, from, next) {
    console.log('before Route leave');
    console.log(to, from);
    if (this.changeSaved) {
      next();
    } else {
      const userWantToLeave = confirm('are you sure? ');
      next(userWantToLeave);
    }
  },
  unmounted() {
    console.log('unmounted');
  }
};
</script>


<style scoped>
ul {
  list-style: none;
  margin: 2rem auto;
  max-width: 20rem;
  padding: 0;
}
</style>