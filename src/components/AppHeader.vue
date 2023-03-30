<script>

export default {
  name: 'AppHeader',
  data() {
    return {
      navLinks: [
        {
          route: '/',
          name: 'home'
        },
        {
          route: 'projects',
          name: 'projects'
        },
        {
          route: 'about',
          name: 'abouts'
        },
        {
          route: 'contacts',
          name: 'contacts'
        }
      ],
      authLinks: [
        {
          route: 'login',
          name: 'login'
        },
        {
          route: 'register',
          name: 'register'
        }
      ]
    }
  }
}
</script>

<template>
  <header>
    <div class="container">
      <nav class="navbar">

        <div class="group">
          <div class="logoContainer">
            logo
          </div>
        </div> <!--/group-->

        <div class="group">
          <ul>
            <li v-for="item in navLinks">
              <router-link :to="item.route">{{ item.name }}</router-link>
            </li>
          </ul>
        </div> <!--/group-->

        <div class="group">
          <ul>
            <li v-for="item in authLinks">
              <router-link :to="item.route">{{ item.name }}</router-link>
            </li>
          </ul>
        </div> <!--/group-->

      </nav>
    </div>
  </header>
</template>

<style lang="scss" scoped>
@use '../style/mixins/mixin.scss' as *;

header {
  padding: 1rem 0;
  margin-bottom: 1.25rem;
  color: white;
  background-color: #343434;
  box-shadow: 0px 2px 16px 1px #ffffff20;
}

.container {}

.logoContainer {
  text-transform: uppercase
}

.navbar {
  @include flexRowSpaceBtwn;

  ul {
    list-style: none;
    @include flexRowCenterGap (1rem);

    li {
      text-transform: capitalize;
      cursor: pointer;

      a {
        color: white;
        text-decoration: none;

        &.router-link-active {
          color: rgb(110, 197, 226);
        }

        &:hover {
          color: lightblue;
        }
      }

    }
  }
}
</style>