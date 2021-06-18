<template>
  <div class="container text-center">
    <h2 class="mb-5">單一產品頁面</h2>
    <p>歡迎來到 " {{ product.title }} " 商品頁面</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      product: {},
    };
  },
  created() {
    console.log(this.$route);
    const { id } = this.$route.params;
    const url = `${process.env.VUE_APP_API}api/${process.env.VUE_APP_PATH}/product/${id}`;
    this.$http
      .get(url)
      .then((res) => {
        console.log(res);
        if (res.data.success) {
          this.product = res.data.product;
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
