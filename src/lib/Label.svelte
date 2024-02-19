<script>
  export let text
</script>

<div class={text.toLowerCase()}>
  {text}
</div>

<style>
  div {
    padding: 4px 8px 4px 8px;
    height: 1rem;
    font-weight: 600;
    border-radius: 0.6rem;
    text-align: center;
  }

  .approved {
    background-color: #188754;
    color: white;
  }
  
  .pending {
    background-color: #FFC10A;
    color: white;
  }
  
  .rejected {
    background-color: #DC3544;
    color: white;
  }
  </style>