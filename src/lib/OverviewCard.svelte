<script>
  export let mainTitle
  export let subTitle
  export let icon
  export let mainNumber
  export let delta
  export let direction
  export let theme
</script>

<section>
  <h2>{mainTitle} <span> | {subTitle}</span></h2>
  <div>
    <i class="bi {icon} {theme}"></i>
    <div>
      <h1>{mainNumber}</h1>
      <h3>{delta} {direction}</h3>
    </div>
  </div>
</section>

<style>
  section {
    padding: 2rem 1rem 2rem 1rem;
    text-align: center;
    border-radius: 10px;
    border: 1px solid grey;
    background-color: white;
  }

  section h2 {
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 2rem;
  }

  section h2 span {
    font-size: 1rem;
    font-weight: 400;
    color: grey;
  }

  section>div {
    display: grid;
    grid-template-columns: 2fr 3fr;
    align-items: center;
    background-color: white;
  }

  section>div>div h1 {
    font-size: 2.25rem;
  }

  section>div>i {
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 800;
    font-size: 2.5rem;
    height: 4rem;
    width: 4rem;
    border-radius: 50%;
  }

  .green {
    background-color: #E0F8E9;
    color: #2DCA6A;
  }

  .blue {
    background-color: #F6F6FE;
    color: #4154F1;
  }

  .salmon {
    background-color: #FFECDF;
    color: #FF771E;
  }
</style>