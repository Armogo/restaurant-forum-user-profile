<template>
  <div class="container py-5">
    <form @submit.stop.prevent="handleSubmit">
      <div class="form-group">
        <label for="name">Name</label>
        <input
          id="name"
          type="text"
          name="name"
          class="form-control"
          placeholder="Enter Name"
          required
          v-model="currentUser.name"
        />
      </div>

      <div class="form-group">
        <label for="image">Image</label>
        <img
          v-if="currentUser.image"
          :src="currentUser.image"
          class="d-block img-thumbnail mb-3"
          width="200"
          height="200"
        />
        <input
          id="image"
          type="file"
          name="image"
          accept="image/*"
          class="form-control-file"
          @change="handleFileChange"
        />
      </div>

      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
  </div>
</template>

<script>
const dummyUser = {
  currentUser: {
    id: 1,
    name: "管理者",
    email: "root@example.com",
    image: "https://i.imgur.com/58ImzMM.png",
    isAdmin: true,
  },
  isAuthenticated: true,
};

export default {
  data() {
    return {
      currentUser: {
        name: "",
        image: "",
      },
    };
  },

  methods: {
    fetchUser(id) {
      console.log(id);
      this.currentUser = {
        ...this.currentUser,
        ...dummyUser.currentUser,
      };
    },
    handleFileChange(e) {
      const { files } = e.target;

      if (files.length === 0) {
        // 使用者沒有選擇上傳的檔案
        this.currentUser.image = "";
      } else {
        // 否則產生預覽圖
        const imageURL = window.URL.createObjectURL(files[0]);
        this.currentUser.image = imageURL;
      }
    },
    handleSubmit(e) {
      const form = e.target;
      const formData = new FormData(form);
      for (let [name, value] of formData.entries()) {
        console.log(name + ": " + value);
      }
    },
  },

  created() {
    const { id } = this.$route.params;
    this.fetchUser(id);
  },
};
</script>