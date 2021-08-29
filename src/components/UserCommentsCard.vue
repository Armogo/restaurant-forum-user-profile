<template>
  <div class="card">
            <div class="card-header">
              <strong>{{userComments.length}}</strong> 已評論餐廳
            </div>
            <div class="card-body">
                <router-link 
                  :to="{name: 'restaurant', params: {id: comment.RestaurantId}}"
                  v-for="comment in userComments"
                  :key="comment.id"                  
                >
                  <img 
                    :src="comment.Restaurant.image || 'https://loremflickr.com/320/240/restaurant,food/?random=42.58020446504014'" 
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
    'userComments': {
      type: Array,
      required: true
    }
  }
}
</script>