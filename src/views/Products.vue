<template>
  <div class="container">
    <h2 class="text-center mb-5">產品頁面</h2>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">商品名稱</th>
          <th scope="col">產品類別</th>
          <th scope="col">商品原價</th>
          <th scope="col">商品售價</th>
          <th scope="col">商品連結</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in products" :key="item.id">
          <th scope="row">{{ index + 1 }}</th>
          <td>{{ item.title }}</td>
          <td>{{ item.category }}</td>
          <td>{{ item.origin_price }}</td>
          <td>{{ item.price }}</td>
          <td>
            <button type="button" class="btn btn-warning btn-sm" @click="gotopage(item)">
              開啟連結
            </button>
          </td>
          <!-- <td>
            <router-link v-bind:to="`/product/${item.id}`" target="_blank">
              <button type="button" class="btn btn-warning btn-sm">開啟連結</button>
            </router-link>
          </td> -->
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  data() {
    return {
      products: [],
    };
  },
  methods: {
    gotopage(item) {
      // 進入單一頁面可使用 this.$router 查詢方法，可使用 push
      // console.log(this.$router);
      this.$router.push(`/product/${item.id}`);
    },
  },
  created() {
    const url = `${process.env.VUE_APP_API}api/${process.env.VUE_APP_PATH}/products`;
    this.$http
      .get(url)
      .then((res) => {
        console.log(res);
        if (res.data.success) {
          this.products = res.data.products;
        } else {
          console.log(res.data.messages);
        }
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>
