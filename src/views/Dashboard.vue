<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
      <router-link class="navbar-brand" to="/admin">後台導覽列</router-link>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link class="nav-link" to="/admin/DashboardProducts">後台產品列表</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <div class="container text-center">
    <h1 class="py-3">後台首頁</h1>
  </div>
  <router-view></router-view>
</template>
<script>
export default {
  data() {
    return {
      check: false,
    };
  },
  created() {
    // ------ 取出 Token
    const token = document.cookie.replace(
      /(?:(?:^|.*;\s*)carrieHexToken\s*=\s*([^;]*).*$)|^.*$/,
      '$1',
    );
    // ------ 所有 axios 請求都會加上 token
    this.$http.defaults.headers.common.Authorization = token;
    // API文件 - 檢查用戶是否仍持續登入
    const api = `${process.env.VUE_APP_API}api/user/check`;
    this.$http.post(api).then((res) => {
      if (res.data.success) {
        this.check = true;
      } else {
        this.$router.push('/login');
      }
    });
  },
};
</script>
