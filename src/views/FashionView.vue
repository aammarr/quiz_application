<template>
  <section class="custom-row">
    <div class="tw-flex tw-flex-column" style="margin: 0 0 60px 0">
      <header>
        <img class="custom_logo" src="/src/assets/logos/logo_fashion.svg" />
      </header>

      <h2 style="margin: 20px 0">For Girl</h2>

      <div v-for="(row, index) in femaleJson" :key="`$fashion-{index}`">
      <div 
        class="cards tw-mx-auto"
        v-for="(femaleItems, subIndex) in row.data"
        :key="femaleItems.id"
        :class="{ activeImg: activeIndex === index }"
        @click="setActive(index, subIndex)"

      >
        <div class="estate_image" style="position: relative">
          <img
          v-if="activeIndex === index" 
          height="32" width="32" style="object-fit: contain; position: absolute; bottom: -60px;"
          src="/src/assets/icons/icon-circled-arrow.svg" >
          <img
            class="activeImg"
            style="object-fit: cover;"
            :src="`/src/assets/images/fashion/female/${femaleItems.thumbnail.filename}`"
          />
        </div>
        <div class="estate_info">
          <div>
            <h6>{{ femaleItems.name }}</h6>
            <img
              height="32"
              :src="
                femaleItems.options
                  ? `/src/assets/images/avatars/${femaleItems.options.agent.avatar.filename}`
                  : '/src/assets/Image/user_placeholder.png'
              "
            />
            <p class="name">{{ null || "Anonymous" }}</p>
          </div>
          <div>
            <p class="price">
              ${{ femaleItems.price || 0 }} <small>per week</small>
            </p>
          </div>
        </div>
      </div>
      </div>

      <h2 style="margin: 20px 0">For Men</h2>

      <div v-for="(row, index) in maleJson" :key="`$fashion-{index}`">
      <div 
        class="cards tw-mx-auto"
        v-for="(maleItems, subIndex) in row.data"
        :key="maleItems.id"
        :class="{ activeImg: activeIndex === index }"
        @click="setActive(index, subIndex)"

      >
        <div class="estate_image" style="position: relative">
          <img
          v-if="activeIndex === index" 
          height="32" width="32" style="object-fit: contain; position: absolute; bottom: -60px;"
          src="/src/assets/icons/icon-circled-arrow.svg" >
          <img
            class="activeImg"
            style="object-fit: cover;"
            :src="`/src/assets/images/fashion/male/${maleItems.thumbnail.filename}`"
          />
        </div>
        <div class="estate_info">
          <div>
            <h6>{{ maleItems.name }}</h6>
            <img
              height="32"
              :src="
                maleItems.options
                  ? `/src/assets/images/avatars/${maleItems.options.agent.avatar.filename}`
                  : '/src/assets/Image/user_placeholder.png'
              "
            />
            <p class="name">{{ null || "Anonymous" }}</p>
          </div>
          <div>
            <p class="price">
              ${{ maleItems.price || 0 }} <small>per week</small>
            </p>
          </div>
        </div>
      </div>
      </div>
    </div>

    <footer class="realEstate_footer">
      <ui-button
        :class="{ fashionSale_btn: selectedFashion }"
        :disabled="!selectedFashion"
        unelevated
        >Select Fashion</ui-button
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
      selectedFashion: null,
    };
  },
  methods: {
    setActive(index, subIndex) {
      this.activeIndex = index;
      // storing selected property.
      this.selectedFashion = this.femaleJson[index].data[subIndex];
    },
    getImagePath(name) {
      if (name) return `/src/assets/images/properties/` + name;
    },
  },
  computed: {
    femaleJson() {
      return jsonData.screens.fashion.female;
    },
    maleJson() {
      return jsonData.screens.fashion.male;
    }
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
  background-color: #e99bcb;
}

.cards {
  width: 385px;
  max-height: 365px;
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
.fashionSale_btn {
  background-color: #971381 !important;
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
