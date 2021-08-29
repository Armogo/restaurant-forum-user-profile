<template>
  <div class="card">
            <div class="card-header">
              <strong>{{userFollowers.length}}</strong> followers (追隨者)
            </div>
            <div class="card-body">
                <router-link 
                  :to="{name: 'user', params: {id: user.id}}"
                  v-for="user in userFollowers"
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
    'userFollowers': {
      type: Array,
      requried: true
    }
  }
}
</script>