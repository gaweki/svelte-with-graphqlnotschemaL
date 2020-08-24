<script>
  import Banner from "./Banner.svelte"
  import Title from "./Title.svelte"
  import List from "./List.svelte"
  import SubFooter from "@/components/sub-footer"
</script>

<style>
  .container-body{
    margin-top: 34px;
  }
  .container-list{
    width: 1280px;
    margin-right: auto;
    margin-left: auto;
    margin-top: 2rem;
    overflow: hidden;
  }
</style>

<div class="container-body">
  <Banner />
  <div class="container-list">
    <Title />
    <List />
  </div>
</div>
<SubFooter />
