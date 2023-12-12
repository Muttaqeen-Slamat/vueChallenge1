<template>
  <div class="wrapper">
    <select v-model="baseVal">
      <option value="Keyboard">Keyboard</option>
      <option v-for="cater in categories" :key="cater">{{ cater }}</option>
    </select>

    <div v-if="category.length">
      <div class="prodCard" v-for="item in category" :key="item.id">
        <div class="card-header">
          <h2>{{ item.name }}</h2>
        </div>
        <div class="card-body">
          <img :src="item.image" :alt="item.name" loading="lazy">
          <p :class="item.price">R{{ item.price }}</p>
        </div>
        <div class="card-footer">
          <p>{{ item.spec }}</p>
        </div>
      </div>
    </div>
    <div v-else>
      <p>No item Found in this Catergory</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      products: [
      {
          id: 1,
          name: "Logitech G915",
          price: 5000,
          image: "https://i.postimg.cc/W40F76VW/Logitech-G915.png",
          spec: "Tenkeyless, Wireless, Mechanical, Low Profile, Switch Options, Lightsync RGB, Tactile",
        },
        {
          id: 2,
          name: "Higround BLACKICE",
          price: 2500,
          image:
            "https://i.postimg.cc/kgmRcQWh/Screenshot-2023-12-05-092527.png",
          spec: "65% Keyboard, Wireless, Mechanical, Hot Swappable Switches, PBT Keycaps, Dedicated Arrow Keys, White Flame Switch",
        },
        {
          id: 3,
          name: "Corsair K100 - Midnight Gold",
          price: 3000,
          image:
            "https://i.postimg.cc/SNzbx1N2/Screenshot-2023-12-05-094839.png",
          spec: "Aluminum design, RGB, Corsair OPX Switches, Media Control, ICUE Wheel, Linear Key Switches, 1.0mm Actuation, Macro Keys",
        },
        {
          id: 4,
          name: "Da Vinci Resolve Editor",
          price: 10000,
          image:
            "https://i.postimg.cc/jjN17c88/Screenshot-2023-12-05-102115.png",
          spec: "Search Dial Control, Wired USB Type-C or Wireless, USB Hub, Metal Design, Dedicated Keys, Design for Desktop",
        },
        {
          id: 5,
          name: "Razer Huntsman Mini",
          price: 750,
          image: "https://i.postimg.cc/NjV5f3jr/Razer-Huntsman-mini.jpg",
          spec: " 60%, Wired, Onboard Memory, PBT Keycaps, Clicky Optical Switches, Chroma RGB Lightning",
        }
      ],
      categories: ['GPUs', 'Mouse','Headsets'],
      baseVal: 'Keyboard'
    };
  },
  computed: {
    category() {
      let filterOut = this.products;
      if (this.baseVal !== 'Keyboard') {
        filterOut = filterOut.filter(product => product.category === this.baseVal);
      }
      return filterOut;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  margin-top: 60px;
  background-color: rgb(132, 127, 127);
}

img{
  width: 16rem;
}
select{
  background-color: black;
  color: #ffffff;
}

</style>
