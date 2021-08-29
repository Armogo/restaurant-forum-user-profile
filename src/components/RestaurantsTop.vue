<template>
  <div class="row no-gutters">
        <div class="col-md-4">
          <a href="#">
            <img
              class="card-img"
              :src="restaurant.image || 'https://loremflickr.com/320/240/food,dessert,restaurant/?random=2'"
            >
          </a>
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">
              {{restaurant.name}}
            </h5>
            <span class="badge badge-secondary">收藏數：{{restaurant.FavoriteCount}}</span>
            <p class="card-text">
              {{restaurant.description}}
            </p>
            <a
              href="#"
              class="btn btn-primary mr-2"
              @click.stop.prevent="showRestaurant"
            >Show</a>

            <button
              type="button"
              class="btn btn-danger mr-2"
              v-if="restaurant.isFavorited"
              @click.stop.prevent="deleteFavorite"
            >
              移除最愛
            </button>
            <button
              type="button"
              class="btn btn-primary"
              v-else
              @click.stop.prevent="addFavorite"
            >
              加到最愛
            </button>
          </div>
        </div>
      </div>
</template>

<script>
export default {
  props: {
    'initialRestaurant': {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      restaurant: this.initialRestaurant
    }
  },
  methods: {
    showRestaurant() {

    },
    addFavorite() {
      this.restaurant.isFavorited = true
    },
    deleteFavorite() {
      this.restaurant.isFavorited = false
    }
  }
}
</script>