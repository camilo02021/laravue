<template>
  <div class="app-container">
    <el-form v-if="user" :model="user">
      <el-row :gutter="20">
        <el-col :span="6">
          <user-card :user="user" />
          <user-bio />
        </el-col>
        <el-col :span="18">
          <user-activity :user="user" />
        </el-col>
      </el-row>
    </el-form>
  </div>
</template>

<script>
import Resource from '@/api/resource';
import UserBio from './components/UserBio.vue';
import UserCard from './components/UserCard.vue';
import UserActivity from './components/UserActivity.vue';

const userResource = new Resource('users');
export default {
  name: 'EditUser',
  components: { UserBio, UserCard, UserActivity },
  data() {
    return {
      user: {},
    };
  },
  watch: {
    '$route': 'getUser',
  },
  created() {
    const id = this.$route.params && this.$route.params.id;
    const currentUserId = this.$store.getters.userId;
    if (id === currentUserId) {
      this.$router.push('/profile/edit');
      return;
    }
    this.getUser(id);
  },
  methods: {
    async getUser(id) {
      const { data } = await userResource.get(id);
      this.user = data;
    },
  },
};
</script>
