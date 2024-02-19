<script>
  export let time
  export let color
  export let activity
</script>


<div class="time-line-item">
  <div>{time}</div>
  <div class="dot {color}"></div>
  <div class="line"></div>
  <div class="activity">{activity}</div>
</div>

<style>
  .time-line-item {
    display: grid;
    grid-template-columns: 3.5rem 1rem 1rem 1fr;
    /* margin-top: 2rem; */
  }

  .dot, .line {
    position: relative;
  }

  .dot {
    width: 18px;
    height: 18px;
    border-radius: 8px;
    top: 2px;
  }

  .line {
    height: 3rem;
    left: -16px;
  }

  .line {
    border-left: 2px solid grey;
  }

  .green {
    background-color: #188754;
  }

  .red {
    background-color: #DC3544;
  }

  .blue {
    background-color: #0E6EFD;
  }

  .aqua {
    background-color: #0DCAF0;
  }

  .yellow {
    background-color: #FFC10A;
  }

  .grey {
    background-color: #5C5F65;
  }
</style>