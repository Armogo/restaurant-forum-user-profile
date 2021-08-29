<template>
  <div class="card">
            <div class="card-header">
              <strong>{{userFollowings.length}}</strong> followings (追蹤者)
            </div>
            <div class="card-body">
                <router-link 
                  :to="{name: 'user', params: {id: user.id}}"
                  v-for="user in userFollowings"
                  :key="user.id"
                >
                    <img 
                      :src="user.image || 'https://i.imgur.com/WMsHuNP.jpeg'" 
                      width="60" 
                      height="60" 
                      class="avatar"
                    >
                </router-link>                
            </div>
          </div>
</template>

<script>
export default {
  props: {
    'userFollowings': {
      type: Array,
      required: true
    }
  }
}
</script>