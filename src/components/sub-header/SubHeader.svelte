<script>
  import Socmeds from '@/components/socmeds';
</script>

<style type="text/scss">
  .subheader-container{
    opacity: 1;
    margin-right: auto;
    margin-left: auto;
    height: 42px;
    z-index: 4;
    display: flex;
    top: 0px;
    right: 0px;
    left: 0px;
    position: fixed;
    -webkit-box-align: center;
    align-items: center;
    font-size: 14px;
    background: 0% 0% no-repeat padding-box padding-box rgb(245, 245, 245);
    padding: 0px 6.1%;
  }
  .title-download{
    -webkit-box-flex: 1;
    flex-grow: 1;
  }
  .container-socmeds{
    display: flex;
    div{
      color: rgb(80, 80, 80);
      white-space: pre;
      float: left;
      cursor: pointer;
    }
  }
</style>

<div class="subheader-container">
  <div class="title-download">Download Tokodistributor App</div>
  <div class="container-socmeds"><div>Follow us on: </div><Socmeds /></div>
</div>