<template>
  <div id="user" class="user" v-if="user">
    <div style="margin-left: .4rem;" class="user-author-avatar" v-if="img">
      <img :src="img" :alt="user.name"/>
    </div>
    <div class="user-details flex">
      <div>
        <h3 class="user-name">{{ user.name }}</h3>
        <div class="user-username">{{ user.username }}</div>
        <div class="user-username">{{ user.email }}</div>
        <div class="user-username">{{ user.phone }}</div>
        <div class="user-username">{{ user.address.street }}</div>
        <div class="user-username">{{ user.address.city }}</div>
        <div class="user-username">{{ user.address.zipcode }}</div>
      </div>
      <div class="user-meta">
        <div class="user-extra" style="text-align: center;">Extra info</div>
        <div class="user-extra">website : <a href="#" target="_blank">{{ user.website }}</a></div>
        <div class="user-extra">Company : {{ user.company.name }}</div>
        <div class="user-extra">{{ user.company.catchPhrase }}</div>
        <div class="user-extra">{{ user.company.bs }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    user: {
      type: Object
    },
    img: {
      type: String
    }
  }
}
</script>

<style lang="scss" scoped>
  $accent-color: #ff9800;
  #user {
    background: #fff;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  }
  #user:hover {
    background-color: lighten($accent-color, 30);
  }
  .user {
    --avatar-size: 80px;
    display: flex;
    align-items: center;
    padding: 32px 0;
    position: relative;
    transition: all .3s;
    &:hover {
      opacity: .85;
      background-color: lighten($accent-color, 30);
      border-radius: 5px;
    }
    &-username {
      font-size: .85rem;
    }
    &-author-avatar {
      width: var(--avatar-size);
      height: var(--avatar-size);
      border-radius: 50%;
      z-index: 2;
      overflow: hidden;
      & img {
        width: var(--avatar-size);
        height: var(--avatar-size);
      }
    }
    &-details {
      width: 100%;
      display: flex;
      flex-direction: column;
      text-align: left;
      padding: 1em;
    }
    &-extra {
      text-align: left;
      font-style: italic;
      font-weight: bold;
    }
    &-name {
      margin: 0;
    }
    &-meta {
      color: #888;
      margin-bottom: 0;
      text-align: left;
    }
  }
  .flex {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
</style>
