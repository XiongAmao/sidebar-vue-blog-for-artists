<template>
  <div class="container">
    <Sidebar>
      <ul class="sidebar-panel-nav">
        <li><a href="./myposts">Blog</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </Sidebar>
    <nav class="main-nav">
      <div class="logo">
        Everyone is an Artist
      </div>
    </nav>

    <div class="container2">
      <div class="gallery">
        <div
          v-for="(img, idx) in imgs"
          :key="idx"
          class="pic"
          @click="() => show(idx)"
        >
          <img :src="img.src ? img.src : img" />
        </div>

        <Logo />
        <h1 class="title">
          Hiii
        </h1>

        <div class="links">
          <a
            href="./myposts"
            target="_blank"
            rel="noopener noreferrer"
            class="button--green"
          >
            My Posts
          </a>
          <a
            href="https://github.com/nuxt/nuxt.js"
            target="_blank"
            rel="noopener noreferrer"
            class="button--grey"
          >
            GitHub
          </a>
        </div>
        <client-only>
          <vue-easy-lightbox
            :visible="visible"
            :index="index"
            :imgs="imgs"
            @hide="visible = false"
            @on-prev="handlePrev"
            @on-next="handleNext"
          />
        </client-only>
      </div>
    </div>
  </div>
</template>

<script>
import Sidebar from "../components/Sidebar.vue";

export default {
  name: "index",
  components: {
    Sidebar
  },
  data() {
    return {
      imgs: [
        "http://placekitten.com/800/600",
        "~/assets/dancing1.jpg",
        "https://via.placeholder.com/250.png/09f/fff?text=second+img"
      ],
      visible: false,
      index: 0 // default
    };
  },
  methods: {
    show(index) {
      this.index = index;
      this.visible = true;
    },
    handlePrev(oldIndex, newIndex) {
      console.log("when next btn click ----");
      console.log("oldIndex of imgs:", oldIndex);
      console.log("newIndex of imgs:", newIndex);
    },
    handleNext(oldIndex, newIndex) {
      console.log("when next btn click ----");
      console.log("oldIndex of imgs:2", oldIndex);
      console.log("newIndex of imgs: 3", newIndex);
      if (newIndex === this.imgs.length - 1) {
        this.addImg();
      }
    },
    addImg() {
      this.imgs.push(
        "https://via.placeholder.com/250.png/00a26e/fff?text=new+img"
      );
    }
  }
};
</script>
//list-styletype -> .sidebar-panel-nav li a
<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
}
.burger {
  align-content: right;
  justify-content: right;
}
.imgfun {
  width: 200px;
}
.container2 {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.logo {
  align-self: center;
  color: rgb(248, 7, 7);
  font-weight: bold;
  font-family: "Lato";
}

.main-nav {
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 0.8rem;
}
.sidebar-panel-nav {
  list-style-type: none;
}
.sidebar-panel-nav li a {
  color: rgb(19, 180, 14);
  text-decoration: none;

  font-size: 1.5rem;
  display: block;
  padding-bottom: 0.5em;
  color: rgb(248, 7, 7);
  font-weight: bold;
  font-family: "Lato";
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #26643b;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.gallery {
  display: flex;
}
.pic {
  cursor: pointer;
  margin-right: 8px;
}
</style>
