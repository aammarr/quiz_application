<template>
  <section class="realEstate">
    <header>
      <img class="estate_logo" src="/src/assets/logos/logo_real-estate.svg" />
    </header>
    <ul class="estate_list" style="margin: 0 0 50px 0">
      <li
        v-for="properties, index in myJson"
        :class="{ activeImg: activeIndex === index }"
        @click="setActive(index)"
        :key="properties.id"
        class="estate_item"
      >
        <div class="estate_image">
          <img class="activeImg" :src="getImagePath(properties.thumbnail.filename)" />
        </div>
        <div class="estate_info">
          <div>
            <h6>{{ properties.name }}</h6>
            <img
              :src="`/src/assets/images/avatars/${properties.options.agent.avatar.filename}`"
            />
            <p class="name">{{ properties.options.agent.name }}</p>
          </div>
          <div>
            <p class="price">
              ${{ properties.options.price.weekly_value || 0 }} <small>per week</small>
            </p>
          </div>
        </div>
      </li>
    </ul>
    <footer class="realEstate_footer">
      <ui-button 
      @click="$router.push('/car')"
      :class="{ realEstate_btn: selectedProperty }" :disabled="!selectedProperty" unelevated>Select Property</ui-button>
    </footer>
  </section>
</template>

<script>
import jsonData from "@/data/data.json";
export default {
  data() {
    return {
      activeIndex: null,
      selectedProperty: null,
    };
  },
  methods: {
    setActive(index) {  
      this.activeIndex = index;
      // storing selected property.
      this.selectedProperty = this.myJson[index];
    },
    getImagePath(name) {
      if (name) return `/src/assets/images/properties/` + name;
    },
  },
  computed: {
    myJson() {
      return jsonData.screens.realEstate.data;
    },
  },
};
console.log(jsonData);
</script>

<style scoped>
.activeImg > .estate_image > img {
  filter: grayscale(100%);
}

.realEstate {
  background-color: #f9eded;
  position: absolute;
  width: 100%;
  top: 0%;
  height: 225vh;
}
li {
  list-style: none;
}
.estate_logo {
  position: relative;
  top: 81px;
  left: 50%;
  transform: translateX(-50%);
}
.estate_list {
  background-color: #f9eded;
  display: flex;
  position: relative;
  top: 120px;
  align-items: center;
  flex-direction: column;
}
.estate_info {
  background-color: #ffffff !important;
  border-radius: 20px;
  position: relative;
  bottom: 30px;
  height: 103px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.estate_info h6 {
  font-family: "Nunito";
  font-style: normal;
  font-weight: 400;
  font-size: 20px;
  line-height: 27px;
  letter-spacing: -0.3px;
  color: #143656;
  padding: 15px 0 0 26px;
}
.estate_info img {
  border: 5px solid #ffffff;
  padding: 5px 0 0 26px;
}
.estate_info .name {
  /* font-family: "Rubik"; */
  font-style: normal;
  font-weight: 300;
  font-size: 11px;
  line-height: 13px;
  letter-spacing: -0.3px;
  padding: 0;
  position: relative;
  left: 60px;
  bottom: 25px;
}
.estate_info .price {
  /* font-family: "Rubik"; */
  font-style: normal;
  font-weight: bolder;
  font-size: 20px;
  line-height: 24px;
  letter-spacing: -0.3px;
  color: #143656;
  padding: 0;
  position: relative;
  top: 45px;
  right: 23px;
}
.estate_image img {
  width: 385px;
  border-radius: 21px;
}
.realEstate_footer {
  position: fixed;
  bottom: 0;
  width: 100%;
  background: #ffffff;
  box-shadow: 0px -5px 50px rgba(15, 26, 66, 0.05);
  border-radius: 20px;
  height: 70px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.realEstate_btn {
  background-color: #be1e2d !important;
  border-radius: 10px;
  border: none;
  height: 40px;
  font-family: "Nunito" !important;
  font-weight: 400;
  font-size: 16px;
  line-height: 19px;
  color: #ffffff;
  width: 178px;
  cursor: pointer;
}
</style>
