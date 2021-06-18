<template>
  <div class="container py-5">
    <h1>About 頁面</h1>
    <Form v-slot="{ errors }">
      <Field
        id="email"
        name="email"
        type="email"
        class="form-control"
        :class="{ 'is-invalid': errors['email'] }"
        placeholder="請輸入 Email"
        rules="email|required"
        v-model="user.email"
      ></Field>
      <ErrorMessage name="email" class="invalid-feedback"></ErrorMessage>
    </Form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      user: {},
    };
  },
};
</script>
