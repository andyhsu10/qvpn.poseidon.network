<template>
  <div class="view mac">
    <h3 class="title"><img src="../assets/mac-dark.svg" alt=""> Mac OS</h3>
    <div class="hr"></div>
    <div class="content">
      <div class="wrap">
        <h3><span class="number">1</span>Download v2rayU</h3>
        <p class="info">You can download the v2RayU Client here: <a href="https://github.com/yanue/V2rayU/releases/download/2.2.0/V2rayU.dmg" target="_blank"> V2rayU.dmg</a></p>
        <br><div class="caution">Make sure the client app is up to date.</div>
      </div>
      <div class="wrap">
        <h3><span class="number">2</span>Allow Mac to install v2rayU.</h3>
        <img src="../assets/macos-4.gif" alt=""><br>
      </div>
      <div class="wrap">
        <h3><span class="number">3</span>Copy Configuration</h3>
        <div class="config">
          <h3>Your Configuration</h3>
          <div class="input" id="copy-input" v-on:click="Copy">
            <div id="copy">Tab to copy</div>
            <div class="input-text">vmess://eyJwb3J0IjoiMzI0NDMiLCJwcyI6IkRpc25leVBsdXNfVVMiLCJ0bHMiOiJub25lIiwiaWQiOiI1MzFkNTBjMS0zODU1LTQ3MDMtOTRkYi1hNWQyM2Y5ZWU2ZDYiLCJhaWQiOiI2NCIsInYiOiIyIiwiaG9zdCI6IiIsInR5cGUiOiJub25lIiwicGF0aCI6IiIsIm5ldCI6InRjcCIsImFkZCI6ImRpc25leXBsdXMuM3EudmMifQ==</div>
          </div>
        </div>
      </div>
      <div class="wrap">
        <h3><span class="number">4</span>Click “Import Server From Pasteboard” via v2rayU icon in the menu bar</h3>
        <img src="../assets/macos-1.gif" alt="">
      </div>
      <div class="wrap">
        <h3><span class="number">5</span>Turn to "Global Mode"</h3>
        <img src="../assets/macos-2.png" alt="">
      </div>
      <div class="wrap">
        <h3><span class="number">6</span>Sign up your Disney+ Account</h3>
        <p class="info">Go to <a href="https://www.disneyplus.com/home" target="_blank">Disney+</a> and sign up an account.<br/>If you’d like to take a trial of watching Disney+, our community supports you for Disney + free trial. Come join us!</p>
        <img src="../assets/macos-3.png" alt="">
      </div>
      <div class="done"><h4>🎉 ALL DONE! ENJOY.</h4></div>
    </div>
  </div>
</template>

<script>
import $ from 'jquery'

export default {
  name: 'Copy',
  methods: {
    Copy () {
      CopyToClipboard('vmess://eyJwb3J0IjoiMzI0NDMiLCJwcyI6IkRpc25leVBsdXNfVVMiLCJ0bHMiOiJub25lIiwiaWQiOiI1MzFkNTBjMS0zODU1LTQ3MDMtOTRkYi1hNWQyM2Y5ZWU2ZDYiLCJhaWQiOiI2NCIsInYiOiIyIiwiaG9zdCI6IiIsInR5cGUiOiJub25lIiwicGF0aCI6IiIsIm5ldCI6InRjcCIsImFkZCI6ImRpc25leXBsdXMuM3EudmMifQ==', true, 'Copied!')
      $('#copy').html('Copied!')
      setTimeout(function () { $('#copy').html('Tab to copy') }, 1600)

      function CopyToClipboard (value, showNotification, notificationText) {
        var $temp = $('<input>')
        $('body').append($temp)
        $temp.val(value).select()
        document.execCommand('copy')
        $temp.remove()

        if (typeof showNotification === 'undefined') {
          showNotification = true
        }
        if (typeof notificationText === 'undefined') {
          notificationText = 'Copied to clipboard'
        }

        var notificationTag = $('div.copy-notification')
        if (showNotification && notificationTag.length === 0) {
          notificationTag = $('<div/>', { class: 'copy-notification', text: notificationText })
          $('body').append(notificationTag)

          notificationTag.fadeIn(function () {
            setTimeout(function () {
              notificationTag.fadeOut(function () {
                notificationTag.remove()
              })
            }, 800)
          })
        }
      }
    }
  }
}

</script>

<style lang="scss">
  #nav {
    .btn {
      color: rgba($color: #fff, $alpha: .4);
       &::before {
        opacity: .4 !important;
      }
    }
  }
  #nav a.router-link-exact-active {
    color: rgba($color: #fff, $alpha: 1);
    &::before {
      opacity: 1 !important;
    }
  }
.copy-notification {
  color: #ffffff;
  background-color: #A966FF;
  padding: 20px;
  border-radius: 30px;
  position: fixed;
  top: 50%;
  left: 50%;
  width: 150px;
  margin-top: -30px;
  margin-left: -85px;
  display: none;
  text-align:center;
}
#copy-input {
  z-index: 9;
}
</style>
