<script>
  export let title
  export let subTitle
  export let bottomMargin = '2rem';
</script>

<div>
  <h1 style="margin-bottom: {bottomMargin}">{title} <span>| {subTitle}</span></h1>
</div>

<style>
  h1 {
    color: #012970;
    font-size: 1.3rem;
    font-weight: 700;
  }

  span {
    color: #889BBD;
    font-size: 1rem;
  }
</style>