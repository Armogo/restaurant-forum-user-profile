<template>
  <div class="container py-5">    
    <!-- 餐廳資訊頁 RestaurantDetail -->
    <RestaurantDetail :initial-restaurant="restaurant"/>
    <hr>

    <!-- 餐廳評論 RestaurantComments -->
    <RestaurantComments 
      :restaurant-comments="restaurantComments"
      @after-delete-comment="afterDeleteComment"
    />
    <!-- 新增評論 CreateComment -->
    <CreateComment 
      :restaurant-id="restaurant.id"
      @after-create-comment="afterCreateComment"
    />
  </div>  
</template>

<script>
import RestaurantDetail from './../components/RestaurantDetail.vue'
import RestaurantComments from './../components/RestaurantComments.vue'
import CreateComment from './../components/CreateComment.vue'

const dummyData = {
    "restaurant": {
        "id": 4,
        "name": "Mckayla Hintz",
        "tel": "1-240-532-2429",
        "address": "167 Rogahn Mission",
        "opening_hours": "08:00",
        "description": "Impedit nesciunt ad id delectus magnam aspernatur fugit.",
        "image": "https://loremflickr.com/320/240/restaurant,food/?random=42.58020446504014",
        "viewCounts": 42,
        "createdAt": "2021-07-05T09:58:39.000Z",
        "updatedAt": "2021-08-29T11:41:06.847Z",
        "CategoryId": 4,
        "Category": {
            "id": 4,
            "name": "墨西哥料理",
            "createdAt": "2021-07-05T09:58:39.000Z",
            "updatedAt": "2021-07-05T09:58:39.000Z"
        },
        "FavoritedUsers": [
            {
                "id": 81,
                "name": "test",
                "email": "test@example.com",
                "password": "$2a$10$w5bcczmxLzWr/lE9a6fgz.toso5IO1oetOBMHZJK/fM3mGAEtsrAK",
                "isAdmin": false,
                "image": null,
                "createdAt": "2021-08-25T11:13:24.000Z",
                "updatedAt": "2021-08-25T11:13:24.000Z",
                "Favorite": {
                    "UserId": 81,
                    "RestaurantId": 4,
                    "createdAt": "2021-08-25T11:20:14.000Z",
                    "updatedAt": "2021-08-25T11:20:14.000Z"
                }
            }
        ],
        "LikedUsers": [
            {
                "id": 81,
                "name": "test",
                "email": "test@example.com",
                "password": "$2a$10$w5bcczmxLzWr/lE9a6fgz.toso5IO1oetOBMHZJK/fM3mGAEtsrAK",
                "isAdmin": false,
                "image": null,
                "createdAt": "2021-08-25T11:13:24.000Z",
                "updatedAt": "2021-08-25T11:13:24.000Z",
                "Like": {
                    "UserId": 81,
                    "RestaurantId": 4,
                    "createdAt": "2021-08-25T11:22:44.000Z",
                    "updatedAt": "2021-08-25T11:22:44.000Z"
                }
            }
        ],
        "Comments": [
            {
                "id": 4,
                "text": "Ullam quis debitis.",
                "UserId": 1,
                "RestaurantId": 4,
                "createdAt": "2021-07-05T09:58:39.000Z",
                "updatedAt": "2021-07-05T09:58:39.000Z",
                "User": {
                    "id": 1,
                    "name": "root123",
                    "email": "root@example.com",
                    "password": "$2a$10$K2x6pQHkzPEKzw86x8Tc0.bfW7QVdA2Ls4AXBFkFu7xHG3UgA4Mli",
                    "isAdmin": true,
                    "image": "https://i.imgur.com/WMsHuNP.jpeg",
                    "createdAt": "2021-07-05T09:58:39.000Z",
                    "updatedAt": "2021-08-27T08:16:04.000Z"
                }
            },
            {
                "id": 54,
                "text": "Qui eos odio similique.",
                "UserId": 3,
                "RestaurantId": 4,
                "createdAt": "2021-07-05T09:58:39.000Z",
                "updatedAt": "2021-07-05T09:58:39.000Z",
                "User": {
                    "id": 3,
                    "name": "user2",
                    "email": "user2@example.com",
                    "password": "$2a$10$1UaQ5KZLbMCJztUGRWP/uOtIaKel7TQFHIbozRf4LPysvFLu3UOO6",
                    "isAdmin": false,
                    "image": null,
                    "createdAt": "2021-07-05T09:58:39.000Z",
                    "updatedAt": "2021-08-21T02:03:29.000Z"
                }
            },
            {
                "id": 104,
                "text": "Hic voluptatem dolorem.",
                "UserId": 2,
                "RestaurantId": 4,
                "createdAt": "2021-07-05T09:58:39.000Z",
                "updatedAt": "2021-07-05T09:58:39.000Z",
                "User": {
                    "id": 2,
                    "name": "user1",
                    "email": "user1@example.com",
                    "password": "$2a$10$knlgkc6iz7TSC1RADrSjmukYkaQgIc8JSVp1ltz614/F9SK.h/pqa",
                    "isAdmin": false,
                    "image": null,
                    "createdAt": "2021-07-05T09:58:39.000Z",
                    "updatedAt": "2021-08-21T14:30:09.000Z"
                }
            },
            {
                "id": 271,
                "text": "how are you",
                "UserId": 1,
                "RestaurantId": 4,
                "createdAt": "2021-08-10T06:06:00.000Z",
                "updatedAt": "2021-08-10T06:06:00.000Z",
                "User": {
                    "id": 1,
                    "name": "root123",
                    "email": "root@example.com",
                    "password": "$2a$10$K2x6pQHkzPEKzw86x8Tc0.bfW7QVdA2Ls4AXBFkFu7xHG3UgA4Mli",
                    "isAdmin": true,
                    "image": "https://i.imgur.com/WMsHuNP.jpeg",
                    "createdAt": "2021-07-05T09:58:39.000Z",
                    "updatedAt": "2021-08-27T08:16:04.000Z"
                }
            },
            {
                "id": 281,
                "text": "I am fine",
                "UserId": 1,
                "RestaurantId": 4,
                "createdAt": "2021-08-10T06:06:26.000Z",
                "updatedAt": "2021-08-10T06:06:26.000Z",
                "User": {
                    "id": 1,
                    "name": "root123",
                    "email": "root@example.com",
                    "password": "$2a$10$K2x6pQHkzPEKzw86x8Tc0.bfW7QVdA2Ls4AXBFkFu7xHG3UgA4Mli",
                    "isAdmin": true,
                    "image": "https://i.imgur.com/WMsHuNP.jpeg",
                    "createdAt": "2021-07-05T09:58:39.000Z",
                    "updatedAt": "2021-08-27T08:16:04.000Z"
                }
            },
            {
                "id": 441,
                "text": "good",
                "UserId": 81,
                "RestaurantId": 4,
                "createdAt": "2021-08-25T11:23:36.000Z",
                "updatedAt": "2021-08-25T11:23:36.000Z",
                "User": {
                    "id": 81,
                    "name": "test",
                    "email": "test@example.com",
                    "password": "$2a$10$w5bcczmxLzWr/lE9a6fgz.toso5IO1oetOBMHZJK/fM3mGAEtsrAK",
                    "isAdmin": false,
                    "image": null,
                    "createdAt": "2021-08-25T11:13:24.000Z",
                    "updatedAt": "2021-08-25T11:13:24.000Z"
                }
            }
        ]
    },
    "isFavorited": false,
    "isLiked": false
}

const dummyUser = {
  currentUser: {
    "id": 1,
    "name": "root123",
    "email": "root@example.com",
    "image": "https://i.imgur.com/WMsHuNP.jpeg",
    "isAdmin": true
  },
  isAuthenticated: true
}

export default {
  components: {
    RestaurantDetail,
    RestaurantComments,
    CreateComment
  },
  data() {
    return {
      restaurant: {
        id: -1,
        name: '',
        categoryName: '',
        image: '',
        openingHours: '',
        tel: '',
        address: '',
        description: '',
        isFavorited: false,
        isLiked: false
      },
      restaurantComments: [],
      currentUser: dummyUser.currentUser  
    }
  },
  created() {
    const {id: restaurantId} = this.$route.params
    this.fetchRestaurant(restaurantId)
  },
  methods: {
    fetchRestaurant(restaurantId) {
      const {restaurant, isFavorited, isLiked} = dummyData
      const {
        id, 
        name,
        Category, 
        image, 
        opening_hours: openingHours, 
        tel, 
        address, 
        description
      } = restaurant
      
      console.log(this.$route.params)
      console.log(restaurantId)

      this.restaurant = {
        id,
        name,
        categoryName: Category ? Category.name : '未分類',
        image, 
        openingHours, 
        tel, 
        address, 
        description, 
        isFavorited, 
        isLiked
      }
      this.restaurantComments = restaurant.Comments
    },
    afterDeleteComment (commentId) {
      // 以 filter 保留未被選擇的 comment.id
      this.restaurantComments = this.restaurantComments.filter(
        comment => comment.id !== commentId
      )
    },
    afterCreateComment (payload) {
      const { commentId, restaurantId, text } = payload
      this.restaurantComments.push({
        id: commentId,
        RestaurantId: restaurantId,
        User: {
          id: this.currentUser.id,
          name: this.currentUser.name
        },
        text,
        createdAt: new Date()
      })
    }
  }

}
</script>