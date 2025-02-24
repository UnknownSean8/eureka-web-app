<template>
  <!-- Home screen -->
  <div class="page-pad">
    <div class="home__hero text--center">
      <div class="heading heading--normal">Your Go-To Platform to</div>
      <div class="heading mar__b--2">Network with MUMTEC Talent</div>
      <div class="body home__subtitle mar__t--2 mar__b--2">
        Look no further if you need to find others within the Monash University Malaysia Tech Club (MUMTEC) Community with whom you can team up,
        seek guidance or just simply say hi. We aim to make it easier to find people to join you on your unique
        adventures.
      </div>
      <router-link :to="{ name: 'SignUp'}" v-if="isLoggedIn">
        <Button text="Signup" class="mar--auto mar__t--2 mar__b--2" />
      </router-link>
      <router-link :to="{ name: 'FindTalent'}" v-else>
        <Button text="Find Talent" class="mar--auto mar__t--2 mar__b--2" />
      </router-link>
      <img src="@/assets/home-hero-illustration.svg" class="mar__t--3 mar__b--5 home__hero--img" />
    </div>
    <div class="home__features">
      <div class="row">
        <img src="@/assets/event-illustration.svg" class="feature__image pad--3" />
        <div class="mar--auto">
          <div class="subheading mar__b--2">Explore Events Happening Around You</div>
          <div class="body mar__b--3">
            Go through the list of events to find something you will potentially be
            interested to take part in. You can find upcoming hackathons, datathons, talks,
            workshops and more, all in one location.
          </div>
        </div>
      </div>
      <div class="row feature__order--unchanged">
        <div class="mar--auto">
          <div class="subheading mar__b--2">Meet Talent From The Student Community</div>
          <div class="body mar__b--3">
            Filter and team up with other like-minded students who are just as passionate and
            ambitious as you. You might just find your next teammate for a competition, personal
            project and more!
          </div>
        </div>
        <img src="@/assets/talent-illustration.svg" class="feature__image pad--3" />
      </div>
      <div class="row">
        <img src="@/assets/mentor-illustration.svg" class="feature__image pad--3" />
        <div class="mar--auto">
          <div class="subheading mar__b--2">A Place For Seniors And Alumni To Share Their Expertise</div>
          <div class="body mar__b--5">
            Network with experienced members of the community who are ready to guide you and your team.
            If you are interested to be a mentor, do get in touch with our team or create an account today!
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="home__develop text--center text--white page-pad">
      <div class="heading mar__b--3">Contribute to This Platform</div>
      <div class="body mar__b--3">
        We're going Open Source soon and you'll be able to help build and add features
        to make this platform better! Built by the student community for the community.
      </div>
      <div class="body">Stay tuned for more.</div>
  </div>
  <section class="home__cta page-pad text--center home__team">
    <div class="heading mar__b--2">Meet the Eureka Team</div>
    <div class="team-wrapper">
      <div>
        <img class="home__team--img" src="@/assets/nitin.jpg">
        <div class="subheading">Nitin Mathew</div>
        <div class="body ">Technical Project Manager</div>
      </div>
      <div>
        <img class="home__team--img" src="@/assets/blaise.jpg">
        <div class="subheading">Blaise Tiong</div>
        <div class="body">Frontend Lead</div>
      </div>
      <div>
        <img class="home__team--img" src="@/assets/chantelle.jpeg">
        <div class="subheading">Chantelle Loh</div>
        <div class="body">Community Manager</div>
      </div>
      <div>
        <img class="home__team--img" src="@/assets/minhao.jpeg">
        <div class="subheading">Chee Min Hao</div>
        <div class="body">Community Manager</div>
      </div>
      <div>
        <img class="home__team--img" src="@/assets/weichun.png">
        <div class="subheading">Tan Wei Chun</div>
        <div class="body">Junior Developer</div>
      </div>
      <div> 
        <img class="home__team--img" src="@/assets/sean.jpg">
        <div class="subheading">Sean Leong</div>
        <div class="body">Junior Developer</div>
      </div>
      <div>
        <img class="home__team--img" src="@/assets/sauce.jpeg">
        <div class="subheading">Foong Shee Yao</div>
        <div class="body">Junior Developer</div>
      </div>
    </div>
  </section>
  <div class="home__form page-pad text--center text--white">
      <div class="heading mar__b--2">Ready to Form Your Ultimate Team?</div>
      <div class="body mar__b--3">You solution is just a click away.</div>
      <router-link :to="{ name: 'SignUp'}" v-if="isLoggedIn">
        <Button text="Signup" class="mar--auto mar__t--2 mar__b--2 button__form" />
      </router-link>
      <router-link :to="{ name: 'FindTalent'}" v-else>
        <Button text="Find Talent" class="mar--auto mar__t--2 mar__b--2 button__form" />
      </router-link>
  </div>
  <div class="home__footer pad--3 text--white">
    <div class="home__footer--left">
      <router-link :to="{ name: 'Privacy'}">
        <div class="tagline cursor__pointer margin text--white">Privacy</div>
      </router-link>
      <router-link :to="{ name: 'Terms'}">
        <div class="tagline cursor__pointer margin text--white">Terms & Conditions</div>
      </router-link>
    </div>
    <div>
      <div class="tagline">&copy; {{currentYear}} Eureka Open Source. All rights reserved.</div>
    </div>
  </div>
</template>

<script>
import { computed } from 'vue';
import store from '@/store';
import Button from '@/common/Button.vue';
export default {
  name: 'Home',
  components: { Button },
  setup() {
    // computed properties
    const isLoggedIn = computed(() => !store.state.user);
    const currentYear = computed(() => new Date().getFullYear());
    return { isLoggedIn, currentYear }
  }
}
</script>

<style lang="scss" scoped>
.home {
  &__hero {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    .heading--normal {
        font-weight: $normal;
    }
    &--img {
      width: 500px;
      max-width: 100%;
    }
  }
  &__features {
    .row {
      display: flex;
      max-width: 1000px;
      margin-left: auto;
      margin-right: auto;
    }
    .feature__image {
      height: 300px;
      max-width: 100%;
    }
  }
  &__team {
    .team-wrapper {
      max-width: 1250px;
      width: 100%;
      margin: 0 auto;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-evenly;
    }
    .team-wrapper > div{
      margin: 30px;
    }
    &--img {
      width: 200px;
      height: 200px;
      border-radius: 50%;
      margin-bottom: 20px;
      &:hover {
        transform: scale(1.05); /* (150% zoom - Note: if the zoom is too large, it will go outside of the viewport) */
      }
    }
  }
  &__develop {
    background-color: $color-brand;
  }
  &__footer {
    background-color: $color-dark;
    display: flex;
    justify-content: space-between;
    align-items: center;
    &--left {
      display: flex;
      flex-direction: row;
      .tagline {
        margin-left: 30px;
      }
    }
  }
  &__form {
    background-color: $color-brand;
  }
  &__subtitle {
    max-width: 800px;
  }
}
.button {
  &__form {
    @include gradientAnimation($color-white , $color-white);
    @include shadow;
    font-family: inherit;
    display: block;
    padding: $btn-padding;
    color: $color-dark;
    text-transform: uppercase;
    border: none;
    border-radius: $btn-border-radius;
    z-index: 0;
    &:focus {
        outline: 0;
    }
    &:hover {
        cursor: pointer;
    }
  }
}
@media (max-width: 903px) {
  .home__features {
    .row {
      flex-direction: column-reverse;
      justify-content: center;
      text-align: center;
    }
    .feature__order--unchanged {
      flex-direction: column;
    }
  }
  .home__footer {
    flex-direction: column;
    text-align: center;
    &--left {
      flex-direction: column;
      .tagline {
        margin-left: 0;
      }
    }
  }
  .feature__image {
    padding: 0;
  }
  .margin {
    margin-bottom: $spacer * 1.5;
  }
}
</style>


<!--
<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

@Options({
  components: {
    HelloWorld,
  },
})
export default class Home extends Vue {}
</script>
-->
