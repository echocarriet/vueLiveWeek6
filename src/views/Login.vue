<template>
  <div class="container text-center">
    <h2 class="my-5">登入首頁</h2>
    <div class="container">
      <div class="row justify-content-center">
        <h1 class="h3 mb-3 font-weight-normal">
          請先登入
        </h1>
        <div class="col-8">
          <form id="form" class="form-signin">
            <div class="form-floating mb-3">
              <input
                type="email"
                class="form-control"
                id="username"
                placeholder="name@example.com"
                v-model="user.username"
                required
                autofocus
              />
              <label for="username">Email address</label>
            </div>
            <div class="form-floating">
              <input
                type="password"
                class="form-control"
                id="password"
                placeholder="Password"
                v-model="user.password"
                required
              />
              <label for="password">Password</label>
            </div>
            <button type="button" class="btn btn-lg btn-secondary w-100 mt-3" @click="goToAdmin">
              登入 :D
            </button>
          </form>
        </div>
      </div>
      <p class="mt-5 mb-3 text-muted">
        &copy; 2021~∞ - 六角學院
      </p>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      user: {},
    };
  },
  methods: {
    goToAdmin() {
      const url = `${process.env.VUE_APP_API}admin/signin`;
      this.$http
        .post(url, this.user)
        .then((res) => {
          console.log(res);
          const { token, expired } = res.data;
          if (res.data.success) {
            // 把 token 存到cookies
            document.cookie = `carrieHexToken=${token}; expires=${new Date(expired)}; path=/`;
            // console.log(this.$router);
            this.$router.push('/admin'); // Dashboare.vue
          } else {
            console.log(res.data.message);
          }
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>
