<template>
  <div class="card mb-3">
        <div class="row no-gutters">
          <div class="col-md-4">
              <img src="https://i.imgur.com/WMsHuNP.jpeg" width="300px" height="300px">
          </div>
          <div class="col-md-8">
            <div class="card-body">
              <h5 class="card-title">root123</h5>
              <p class="card-text">
                root@example.com
              </p>
              <ul class="list-unstyled list-inline">
                <li><strong>{{user.profile.Comments.length}}</strong> 已評論餐廳</li>
                <li><strong>{{user.profile.FavoritedRestaurants.length}}</strong> 收藏的餐廳</li>
                <li><strong>{{user.profile.Followings.length}}</strong> followings (追蹤者)</li>
                <li><strong>{{user.profile.Followers.length}}</strong> followers (追隨者)</li>
              </ul>
              <p>
                  <router-link 
                    :to="{name: 'user-edit', params: {id: user.profile.id}}" 
                  >
                    <button 
                      type="submit" 
                      class="btn btn-primary" 
                      @click.stop.prevent="">
                        edit
                    </button>
                  </router-link>
              </p>
            </div>
          </div>
        </div>
      </div>
</template>

<script>

export default {
  props: {
    'user': {
      type: Object,
      required: true
    }
  }  
}
</script>