<template>
  <div class="container">
    <navbar title="Profile"></navbar>
    <scroller class="main">
      <div class="profile-bannar">
        <image class="profile-avatar" :src="user.avatar"></image>
        <text class="profile-username">{{user.username}}</text>
      </div>
      <div class="profile-groups">
        <div class="profile-groups-item">
          <text class="">{{user.email}}</text>
        </div>
        <div class="profile-groups-item">
          <text class="">{{user.cellphone}} </text>
        </div>
        <div class="profile-groups-item" @click="openMap()">
          <text class="profile-item-text">{{user.address}}  </text>
          <icon src="http://img1.vued.vanthink.cn/vuedef837912bd199882fd65556b65287ebb.png"></icon>
        </div>
      </div>
      <div class="profile-groups">
        <div class="profile-groups-item">
          <text class="">Account</text>
        </div>
        <div class="profile-groups-item">
          <text class="">Notification and Sounds</text>
        </div>
        <div class="profile-groups-item">
          <text class="">Settings</text>
        </div>
      </div>
      <div class="profile-groups">
        <div class="profile-groups-item">
          <text class="">Report a problem</text>
        </div>
        <div class="profile-groups-item">
          <text class="">Help</text>
        </div>
        <div class="profile-groups-item">
          <text class="">Privacy and Terms</text>
        </div>
      </div>
    </scroller>
    <footer active="3"></footer>
  </div>
</template>
<style>
  .container{
    position: relative;
    flex:1;
    flex-direction: column;
    background-color: #e3e3e3;
    padding-top: 88px;
  }
  .main{
    flex: 1;
    position: relative;
    background-color: #e3e3e3;
    min-height: 400;
    border-bottom-width: 10;
    border-bottom-color: #fff;
  }
  .profile-bannar{
    height: 380px;
    align-items: center;
    justify-content: center;
    background-image: linear-gradient(to left,#00c6ff , #0072ff);
  }
  .profile-avatar{
    width: 200px;
    height: 200px;
    margin-bottom: 20px;
  }
  .profile-username{
    font-size: 40px;
    font-weight: 100;
    color: #fff;
  }
  
  .profile-groups{
    margin-top: 40px;
    padding-top: 10px;
    padding-left: 20px;
    padding-right: 20px;
    background-color: #fff;
    border-top:2px solid rgba(0,0,0,.1);
    border-bottom: 2px solid rgba(0,0,0,.3);
  }
  .profile-groups-item{
    flex-direction: row;
    align-items: center;
    height: 90px;
    border-bottom: 2px solid rgba(0,0,0,.1);
    color: #555;
  }
  .profile-item-text{
    flex: 1;
  }
</style>

<script>
  import navbar from './include/navbar.vue';
  import footer from './include/footer.vue';
  import icon from './include/icon.vue';
  import helper from './lib/helper';
  const naviagtor = weex.requireModule('navigator');
  module.exports = {
    components: {
      'navbar': navbar,
      'footer': footer,
      'icon': icon
    },
    data() {
      return {
        user: {
          avatar: 'http://img1.vued.vanthink.cn/vued4eff4743ed47b7d8add8e7969a5d16cd.png',
          username: 'Tom',
          email: 'tom@gamil.com',
          cellphone: '+86 12345678912',
          address: 'Beijing China'
        }
      }
    },
    methods: {
      openMap() {
        const url = helper.setBundleUrl('pages/map.js', weex);
        naviagtor.push({
          url: url
        })
      }
    }
  }
</script>
