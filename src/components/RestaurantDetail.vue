<template>
  <div class="row">
    <div class="col-md-12 mb-3">
      <h1>{{restaurant.name}}</h1>
      <p class="badge badge-secondary mt-1 mb-3">
        {{restaurant.categoryName}}
      </p>
    </div>
    <div class="col-lg-4">
      <img
        class="img-responsive center-block" 
        :src="restaurant.image || 'https://loremflickr.com/320/240/food,dessert,restaurant/'"
        style="width: 250px;margin-bottom: 25px;"
      >
      <div class="contact-info-wrap">
        <ul class="list-unstyled">
          <li>
            <strong>Opening Hour:</strong>
            {{restaurant.openingHours}}
          </li>
          <li>
            <strong>Tel:</strong>
            {{restaurant.tel}}
          </li>
          <li>
            <strong>Address:</strong>
            {{restaurant.address}}
          </li>
        </ul>
      </div>
    </div>
    <div class="col-lg-8">
      <p>{{ restaurant.description }}</p>
      <router-link
        class="btn btn-primary btn-border mr-2"
        :to="{name: 'dashboard', params: {id: restaurant.id}}"
      >
        Dashboard
      </router-link>

      <button
        type="button"
        class="btn btn-danger btn-border mr-2"
        v-if="restaurant.isFavorited"
        @click.stop.prevent="deleteFavorite"
      >
        移除最愛
      </button>
      <button
        type="button"
        class="btn btn-primary btn-border mr-2"
        v-else
        @click.stop.prevent="addFavorite"
      >
        加到最愛
      </button>
      <button
        type="button"
        class="btn btn-danger like mr-2"
        v-if="restaurant.isLiked"
        @click.stop.prevent="deleteLike"
      >
        Unlike
      </button>
      <button
        type="button"
        class="btn btn-primary like mr-2"
        v-else
        @click.stop.prevent="addLike"
      >
        Like
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    'initialRestaurant': {
      type: Object,
      requried: true
    }
  },
  data() {
    return {
      restaurant: this.initialRestaurant
    }
  },
  methods: {
    addFavorite() {
      this.restaurant = {
        ... this.restaurant,
        isFavorited: true
      }
    },
    deleteFavorite() {
      this.restaurant = {
        ... this.restaurant,
        isFavorited: false
      }
    },
    addLike() {
      this.restaurant = {
        ... this.restaurant,
        isLiked: true
      }
    },
    deleteLike() {
      this.restaurant = {
        ... this.restaurant,
        isLiked: false
      }
    }
  }
}
</script>