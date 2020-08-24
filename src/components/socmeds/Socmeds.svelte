<script>
  import Icon from 'svelte-awesome';
  import { twitter, facebook, instagram, linkedin, youtube } from 'svelte-awesome/icons';
</script>

<style type="text/scss">
  .icons-container{
    display: flex;
  }
  .icon-container{
    color: white;
    width: 24px;
    height: 24px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    margin-right: 6px;
    &.twitter{
      background-color: rgb(80, 137, 208);
    }
    &.facebook{
      background-color: rgb(57, 82, 160);
    }
    &.instagram{
      background-color: rgb(72, 125, 170);
    }
    &.linkedin{
      background-color: rgb(0, 119, 191);
    }
    &.youtube{
      background-color: rgb(223, 18, 0);
    }
  }
</style>

<div class="icons-container">
  <div class="icon-container twitter">
    <Icon style={`width: 14px;height: 14px`} data={twitter}/>
  </div>
  <div class="icon-container facebook">
    <Icon style={`width: 14px;height: 14px`} data={facebook}/>
  </div>
  <div class="icon-container instagram">
    <Icon style={`width: 14px;height: 14px`} data={instagram}/>
  </div>
  <div class="icon-container linkedin">
    <Icon style={`width: 14px;height: 14px`} data={linkedin}/>
  </div>
  <div class="icon-container youtube">
    <Icon style={`width: 14px;height: 14px`} data={youtube}/>
  </div>
</div>