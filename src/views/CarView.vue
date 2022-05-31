<template>
  <section class="custom-row">
    <div class="tw-flex tw-flex-column" style="margin: 0 0 60px 0">
      <header>
        <img class="custom_logo" src="/src/assets/logos/logo_cars-4-sale.svg" />
      </header>

      <div
        class="cards tw-mx-auto"
        v-for="(cars, index) in myJson"
        :class="{ activeImg: activeIndex === index }"
        @click="setActive(index)"
        :key="cars.id"
      >
        <div class="estate_image">
          <img
            class="activeImg"
            :src="`/src/assets/images/cars/${cars.thumbnail.filename}`"
          />
        </div>
        <div class="estate_info">
          <div>
            <h6>{{ cars.name }}</h6>
            <img
              height="32"
              :src="
                cars.options.agent.avatar.filename
                  ? `/src/assets/images/avatars/${cars.options.agent.avatar.filename}`
                  : '/src/assets/Image/user_placeholder.png'
              "
            />
            <p class="name">{{ cars.options.agent.name || "Anonymous" }}</p>
          </div>
          <div>
            <p class="price">
              ${{ cars.options.price.weekly_value || 0 }} <small>per week</small>
            </p>
          </div>
        </div>
      </div>
    </div>

    <footer class="realEstate_footer">
      <ui-button
        :class="{ carSale_btn: selectedCar }"
        :disabled="!selectedCar"
        unelevated
        >Select Car</ui-button
      >
    </footer>
  </section>
</template>

<script>
import jsonData from "@/data/data.json";
export default {
  data() {
    return {
      activeIndex: null,
      selectedCar: null,
    };
  },
  methods: {
    setActive(index) {
      this.activeIndex = index;
      // storing selected property.
      this.selectedCar = this.myJson[index];
    },
    getImagePath(name) {
      if (name) return `/src/assets/images/properties/` + name;
    },
  },
  computed: {
    myJson() {
      return jsonData.screens.carsForSale.data;
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

.custom-row {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: #e3f5f5;
}

.cards {
  width: 385px;
  height: 365px;
  margin: auto;
}

/* .estate_logo {
  position: relative;
  top: 81px;
  left: 50%;
  transform: translateX(-50%);
} */
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
.carSale_btn {
  background-color: #6cdada !important;
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
