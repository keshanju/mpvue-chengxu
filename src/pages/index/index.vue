<template>
  <div @click="clickHandle">
    <div class="userinfo" @click="bindViewTap">
      <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl"/>
      <img class="userinfo-avatar" src="/static/images/user.png"/>
      <div class="userinfo-nickname">
        <card :text="userInfo.nickName"></card>
      </div>
    </div>
    <div class="usermotto">
      <div class="user-motto">
        <card :text="motto"></card>
      </div>
    </div>
    <form class="form-container">
      <input type="text" class="form-control" :value="motto" placeholder="v-model"/>
      <input type="text" class="form-control" v-model="motto" placeholder="v-model"/>
      <input type="text" class="form-control" v-model.lazy="motto" placeholder="v-model.lazy"/>
    </form>
    <div class="all">
      <div class="left">
        11
      </div>
      <div class="right">
        00
      </div>
    </div>
  </div>
</template>

<script>
  import card from "@/components/card";

  export default {
    data() {
      return {
        motto: "Hello miniprograme",
        userInfo: {
          nickName: "mpvue",
          avatarUrl: "http://mpvue.com/assets/logo.png"
        }
      };
    },

    components: {
      card
    },

    methods: {
      bindViewTap() {
        const url = "../logs/main";
        if (mpvuePlatform === "wx") {
          mpvue.switchTab({ url });
        } else {
          mpvue.navigateTo({ url });
        }
      },
      clickHandle(ev) {
        console.log("clickHandle:", ev);
        // throw {message: 'custom test'}
      }
    },

    created() {
      // let app = getApp()
    }
  };
</script>

<style scoped>
  .userinfo {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .userinfo-avatar {
    width: 128 rpx;
    height: 128 rpx;
    margin: 20 rpx;
    border-radius: 50%;
  }

  .userinfo-nickname {
    color: #aaa;
  }

  .usermotto {
    margin-top: 150px;
  }

  .form-control {
    display: block;
    padding: 0 12px;
    margin-bottom: 5px;
    border: 1px solid #ccc;
  }

  .all {
    width: 7.5rem;
    height: 1rem;
    background-color: blue;
  }

  .all:after {
    display: block;
    content: '';
    clear: both;
  }

  .left {
    float: left;
    text-align: center;
    width: 3rem;
    height: 1rem;
    line-height: 1rem;
    background-color: red;
  }

  .right {
    float: left;
    text-align: center;
    width: 4.5rem;
    height: 1rem;
    line-height: 1rem;
    background-color: green;
  }
</style>
