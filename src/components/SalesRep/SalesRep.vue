<template>
  <div class="sales-rep">
    <h3 class="sales-rep__name">
      {{ sales_rep.FirstName }} {{ sales_rep.LastName }}
    </h3>
    <p class="sales-rep__email contact-link">
      <a :href="`mailto: ${sales_rep.EmailAddress}`">{{
        sales_rep.EmailAddress
      }}</a>
    </p>
    <p class="sales-rep__phone contact-link">
      <a :href="`tel: ${sales_rep.Phone}`">{{ sales_rep.Phone }}</a>
    </p>
  </div>
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
.sales-rep {
  text-align: left;

  &__name {
    @include header-underline;
  }

  .contact-link {
    margin: 0 0 .33rem;
    
    a {
      transition: 150ms;
      color: $green;
      
      &:link {
        text-decoration: none;
      }
      &:hover {
        text-decoration: underline;
        opacity: 0.7;
      }
    }
  }
}
</style>
