<template>
  <div>dashboard</div>
</template>

<script>
export default {
  created() {
    const token = document.cookie.replace(
      /(?:(?:^|.*;\s*)hexToken\s*=\s*([^;]*).*$)|^.*$/,
      '$1'
    );
    this.$http.defaults.headers.common.Authorization = token;

    const api = `${process.env.VUE_APP_API}/v2/api/user/check`;

    this.$http.post(api).then((res) => {
      if (!res.data.success) {
        this.$router.push('/login');
      }
    });
  },
};
</script>

<style lang="scss" scoped></style>
