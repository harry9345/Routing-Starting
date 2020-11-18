<template>
  <div>
    <button @click="ConfirmInput">CONFIRM</button>
    <router-view></router-view>
    <ul>
      <teams-item
        v-for="team in teams"
        :id="team.id"
        :key="team.id"
        :name="team.name"
        :member-count="team.members.length"
      ></teams-item>
    </ul>
  </div>
</template>

<script>
import TeamsItem from './TeamsItem.vue';

export default {
  components: {
    TeamsItem
  },
  inject: ['teams'],
  methods: {
    ConfirmInput() {
      // somthings happen
      this.$router.push('/users');
    }
  }
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 2rem auto;
  max-width: 40rem;
  padding: 0;
}
</style>