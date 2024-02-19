<script>
  export let newsItem
</script>

<div class="news-item">
  <img src="{newsItem.image}">
  <span>{newsItem.story}</span>
</div>

<style>
  .news-item {
    display: grid;
    grid-template-columns: 80px 1fr;
    align-items: top;
    column-gap: 12px;
    margin-top: 1.5rem;
    border: 1px solid grey;
    padding: 1rem;
    background-color: white;
  }

  img {
    width: 80px;
    height: 80px;
  }
</style>