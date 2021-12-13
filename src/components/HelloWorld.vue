<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>
      Rover type:
      {{
        rover === "0" ? "Curiosity" : rover === "1" ? "Opportunity" : "Spirit"
      }}
    </h1>
    <div class="gallery">
      <div v-for="item in items.photos" :key="item.id" class="gallery-panel">
        <img :src="item.img_src" h="10" w="10" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
    rover: String,
  },
  watch: {
    rover(newValue) {
      const roverType =
        newValue === "0"
          ? "curiosity"
          : newValue === "1"
          ? "opportunity"
          : "spirit";
      fetch(
        `https://api.nasa.gov/mars-photos/api/v1/rovers/${roverType}/photos?sol=1000&api_key=DEMO_KEY`
      )
        .then((res) => res.json())
        .then((data) => (this.items = data));
    },
  },
  mounted() {
    const roverType =
      this.rover === "0"
        ? "curiosity"
        : this.rover === "1"
        ? "opportunity"
        : "spirit";
    fetch(
      `https://api.nasa.gov/mars-photos/api/v1/rovers/${roverType}/photos?sol=1000&api_key=DEMO_KEY`
    )
      .then((res) => res.json())
      .then((data) => (this.items = data));
  },
  data() {
    return {
      items: [],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(20rem, 1fr));
  grid-gap: 1rem;
  max-width: 80rem;
  margin: 5rem auto;
  padding: 0 5rem;
}

.gallery-panel img {
  width: 100%;
  height: 22vw;
  object-fit: cover;
  border-radius: 0.75rem;
}
</style>
