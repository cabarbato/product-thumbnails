<template>
  <section class="sales-rep">
    <h3 class="sales-rep__name">
      {{ sales_rep.FirstName }} {{ sales_rep.LastName }}
    </h3>
    <p class="sales-rep__location">
      {{ sales_rep.City }}, {{ sales_rep.State }}
    </p>
    <hr />
    <p class="sales-rep__email">
      <a :href="`mailto: ${sales_rep.EmailAddress}`">{{
        sales_rep.EmailAddress
      }}</a>
    </p>
    <p class="sales-rep__phone">
      <a :href="`tel: ${sales_rep.Phone}`">{{ sales_rep.Phone }}</a>
    </p>
  </section>
</template>

<script>
export default {
  name: "SalesRep",
  props: {
    sales_rep: Object,
  },
};
</script>

<style scoped lang="scss">
@import "../../scss/main";
</style>
