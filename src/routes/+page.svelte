<script>
  import OverviewCard from '../lib/OverviewCard.svelte'
  import SectionHeading from '../lib/SectionHeading.svelte'
  import Label from '../lib/Label.svelte'
  import NewsItem from '../lib/NewsItem.svelte'
  import TimeLineItem from '../lib/TimeLineItem.svelte'
  import Chart from '../lib/Chart.svelte'

  let newsItems = [
    {image: 'images/pex01.jpg', story: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Dignissimos sequi sint quam aliquam? Lorem ipsum dolor, sit amet consectetur adipisicing elit. Deleniti et minus corrupti eos reiciendis repudiandae voluptas sit magnam. Animi necessitatibus officiis, exercitationem rerum error soluta ea minima enim.'},
    {image: 'images/pex02.jpg', story: 'Rerum ullam exercitationem cum sed saepe nesciunt ipsa molestias. Ratione nulla dolorum, dolores vel omnis dignissimos voluptas sed ex unde obcaecati voluptas quo numquam? Aut aperiam error ipsa laboriosam, unde id consectetur tenetur quia. Quibusdam corrupti fugiat iste ad perferendis facere nisi tempora quasi quia. Quam, quos?'},
    {image: 'images/pex03.jpg', story: 'Debitis eligendi, consequatur libero quaerat laudantium culpa possimus obcaecati sequi inventore minus accusamus impedit! Pariatur tenetur saepe libero id vel distinctio odio mollitia suscipit optio error iure praesentium. Sit sed alias eos modi enim similique eligendi ullam dolore ut voluptate asperiores quam, beatae nisi dolorem facere a ipsa temporibus rerum aspernatur quibusdam necessitatibus nobis aliquam? Distinctio maiores, a hic perspiciatis non quae iusto sunt fugit, magnam consequuntur id aliquid aut tenetur repudiandae'},
    {image: 'images/pex04.jpg', story: 'Pariatur tenetur saepe libero fugit aliquam maiores, tempore, doloremque quisquam'},
    {image: 'images/pex05.jpg', story: 'Harum explicabo autem ipsam quas quis omnis perferendis unde non et aut laboriosam vitae, quo pariatur officia excepturi quibusdam obcaecati ullam rem molestiae? Earum beatae nisi dolorem facere a ipsa temporibus rerum aspernatur quibusdam necessitatibus nobis aliquam? Distinctio maiores, a hic perspiciatis non quae iusto sunt fugit onsequuntur id aliquid aut tenetur repudiandae, quibusdam itaque necessitatibus nemo amet exercitationem ex unde obcaecati voluptas quo numquam'},
  ]

  let activities = [
    {color: 'green',  activity: 'Quia quae rerum explicabo officiis beatae', time: '32 min'},
    {color: 'red',    activity: 'Voluptatem blanditiis blanditiis eveniet', time: '56 min'},
    {color: 'blue',   activity: 'Voluptates corrupti molestias voluptatem', time: '2 hrs'},
    {color: 'aqua',   activity: 'Tempore autem saepe occaecati voluptatem tempore', time: '1 day'},
    {color: 'yellow', activity: 'Est sit eum reiciendis exercitationem', time: '2 days'},
    {color: 'grey',   activity: 'Dicta dolorem harum nulla eius. Ut quidem quidem sit quas', time: '1 wk'}
  ]

  function adjustSidebarHeight() {
    const sidebar = document.querySelector('aside');
    const pageHeight = Math.max(
      document.body.scrollHeight, document.documentElement.scrollHeight,
      document.body.offsetHeight, document.documentElement.offsetHeight,
      document.body.clientHeight, document.documentElement.clientHeight
    )
  
    sidebar.style.height = pageHeight + 'px'
  }
</script>


<header>
  <div class="left">Nice Admin</div>

  <div class="center">
    <i class="bi bi-list"></i>
    <input type="text" class="page-search" placeholder="Search" />
  </div>

  <div class="right">
    <i class="bi bi-bell"></i>
    <i class="bi bi-chat-left-text"></i>
    <i class="bi bi-person-circle"></i>
    <select name="user">
      <option value="k-anderson">K. Anderson</option>
    </select>
  </div>
</header>
<div></div>
<section class="core">
  <!-- #region navigation -->
  <aside class="navigation">
    <i class="bi bi-grid"></i>
    Dashboard
    <i class="bi bi-hdd-stack"></i>    
    Components
    <i class="bi bi-journal-text"></i>
    Forms
    <i class="bi bi-table"></i>
    Tables
    <i class="bi bi-bar-chart"></i>
    Charts
    <i class="bi bi-gem"></i>
    Icons
    <i class="bi bi-person"></i>
    Profile
    <i class="bi bi-question-circle"></i>
    F.A.Q.
    <i class="bi bi-envelope"></i>
    Contact
    <i class="bi bi-card-list"></i>
    Register
    <i class="bi bi-box-arrow-in-right"></i>
    Login
  </aside>
  <!-- #endregion -->
  <main>
    <div class="page-title">
      <h1>Dashboard</h1>
      <h3>Home / <span>Dashboard</span></h3>
    </div>
    
    <div class="left-right">
      <div class="left">
        <div class="overview">
          <OverviewCard mainTitle="Sales" subTitle="Today" icon="bi-cart" mainNumber="145" delta="12%" direction="increase" theme="blue"/>
          <OverviewCard mainTitle="Revenue" subTitle="This Month" icon="bi-currency-dollar" mainNumber="$3,264" delta="8%" direction="increase" theme="green"/>
          <OverviewCard mainTitle="Customers" subTitle="This Year" icon="bi-people" mainNumber="1244" delta="12%" direction="decrease" theme="salmon"/>
        </div>

        <div class="recent-sales">
          <SectionHeading title="Recent Sales" subTitle="Today" />
          <div class="filters">
            <div class="left">
              <select name="entries" >
                <option value="10">10</option>
                <option value="20">20</option>
                <option value="30">30</option>
              </select>
              <span>entries per page</span>
            </div>

            <div class="right">
              <input type="text" placeholder="Search...">
            </div>
          </div>
          
          <div class="table">
            <div class="th">#</div>
            <div class="th">Customer</div>
            <div class="th">Product</div>
            <div class="th">Price</div>
            <div class="th">Status</div>

            <div class="td">2457</div>
            <div class="td">Brandon Jacob</div>
            <div class="td">Lorem ipsum dolor sit.</div>
            <div class="td">$64</div>
            <Label text="Approved" />

            <div class="td">2147</div>
            <div class="td">Birdie Kessler</div>
            <div class="td">Lorem ipsum dolor sit amet</div>
            <div class="td">$47</div>
            <Label text="Pending" />

            <div class="td">2049</div>
            <div class="td">Ashleigh Langosh</div>
            <div class="td">Adipisicing elit dicta, magni!</div>
            <div class="td">$147</div>
            <Label text="Approved" />

            <div class="td">2644</div>
            <div class="td">Angus Grady</div>
            <div class="td">Vero quod omnis illo</div>
            <div class="td">$67</div>
            <Label text="Rejected" />

            <div class="td">2754</div>
            <div class="td">Raheem Lehner</div>
            <div class="td">Lorem ipsum dolor elit </div>
            <div class="td">$165</div>
            <Label text="Approved" />
          </div>
          <div class="search-summary">
            Showing 1 to 5 of 5 entries
          </div>
        </div>
        <Chart />
      </div>

      <div class="right">
        <div class="recent-activity">
          <SectionHeading title="Recent Activity" subTitle="Today" />
          {#each activities as activity}
            <TimeLineItem color={activity.color} activity={activity.activity} time={activity.time}/>
          {/each}
        </div>
        
        <div class="news">
          {#each newsItems as newsItem}
            <NewsItem {newsItem} />
          {/each}
        </div>
      </div>
    </div>
  </main>
</section>

<style>
  /* #region header */
  header {
    display: grid;
    grid-template-columns: 225px 1fr 1fr;
    align-items: center;
    background-color: white;
    margin-right: -2rem;
    height: 3rem;
    padding: 0 1rem 0 1rem;
  }

  header .left,
  header .center,
  header .right {
    display: flex;
    align-items: center;
  }

  header .right .bi,
  header .right select {
    margin-left: 1rem;
  }

  header .right {
    justify-content: flex-end;
  }

  header .bi {
    font-size: 1.75rem;
  }

  header select {
    height: 1.75rem;
  }
  /* #endregion */
  /* #region core */
  section.core {
    display: grid;
    grid-template-columns: 225px 1fr;
  }
    /* #region aside */
  aside {
    background-color: white;
    /* height: 100vh; */
    display: grid;
    grid-template-columns: 2rem 1fr;
    grid-auto-rows: 2.5rem;
    padding-left: 1.5rem;
    padding-top: 2.5rem;
    position: sticky;
  }
  /* #endregion */
    /* #region main */
    main {
      padding: 2rem 0 2rem 2rem;
    }
    main .page-title h1 {
      font-size: 2rem;
    }

    main .page-title span {
      font-weight: 600;
    }

    main .left .overview {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      column-gap: 2rem;
      margin-top: 2rem;
    }

    main .left .overview div {
      background-color: white;
    }

    main .left .recent-sales {
      margin-top: 2rem;
      padding: 1rem 1rem 1rem 1rem;
      background-color: white;
      border: 1px solid grey;
      border-radius: 10px;
    }
  /* #endregion */

  /* #region filters */
  .filters {
    margin-top: 2rem;
    display: flex;
    justify-content: space-between;
  }  

  .filters select {
    height: 2rem;
    width: 3rem;
  }

  .filters input {
    height: 2rem;
    width: 10rem;
  }
  /* #endregion */

  /* #region table */
  .table {
    margin-top: 2rem;
    display: grid;
    grid-template-columns: 6rem 1fr 1fr 6rem 5.5rem;
    row-gap: 1.5rem;
  }

  .table .th {
    font-weight: 800;
    color: #000;

  }

  /* #endregion */

  .search-summary {
    margin-top: 2.5rem;
    border-top: 1px solid grey;
    padding-top: 2rem
  }

  .left-right {
    display: grid;
    grid-template-columns: 2fr 1fr;
    column-gap: 2rem;
  }

  .recent-activity {
    padding: 1rem;
    background-color: white;
    margin-top: 2rem;
    border: 1px solid grey;
    border-radius: 10px;
  }
</style>
