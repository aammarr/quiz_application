<template>
  <section class="realEstate">
    <header>
      <img class="estate_logo" src="@/assets/svg/logos/logo_real-estate.svg" />
    </header>
    <ul class="estate_list">
      <li v-for="properties in myJson" :key="properties.id" class="estate_item">
        <div class="estate_image">
          <img src="@/assets/images/properties/property_1_starter.jpg" />
        </div>
        <div class="estate_info">
          <div>
            <h6>{{ properties.name }}</h6>
            <img src="@/assets/images/avatars/pete_agent.png" />
            <p class="name">{{ properties.agent }}</p>
          </div>
          <div>
            <p class="price">{{ properties.price }}</p>
          </div>
        </div>
      </li>
      <!-- <li class="estate_item">
        <div class="estate_image">
          <img src="@/assets/images/properties/property_2_flex.jpg" />
        </div>
        <div class="estate_info">
          <div>
            <h6>Flex</h6>
            <img src="@/assets/images/avatars/pete_agent.png" />
            <p class="name">Pete Agent</p>
          </div>

          <div>
            <p class="price">$400 per week</p>
          </div>
        </div>
      </li>
      <li class="estate_item">
        <div class="estate_image">
          <img src="@/assets/images/properties/property_3_midtown.jpg" />
        </div>
        <div class="estate_info">
          <div>
            <h6>Midtown</h6>
            <img src="@/assets/images/avatars/pete_agent.png" />
            <p class="name">Pete Agent</p>
          </div>

          <div>
            <p class="price">$530 per week</p>
          </div>
        </div>
      </li>
      <li class="estate_item">
        <div class="estate_image">
          <img src="@/assets/images/properties/property_4_prestige.jpg" />
        </div>
        <div class="estate_info">
          <div>
            <h6>Prestige</h6>
            <img src="@/assets/images/avatars/pete_agent.png" />
            <p class="name">Pete Agent</p>
          </div>

          <div>
            <p class="price">$680 per week</p>
          </div>
        </div>
      </li>
      <li class="estate_item">
        <div class="estate_image">
          <img src="@/assets/images/properties/property_5_vista.jpg" />
        </div>
        <div class="estate_info">
          <div>
            <h6>Vista</h6>
            <img src="@/assets/images/avatars/pete_agent.png" />
            <p class="name">Pete Agent</p>
          </div>

          <div>
            <p class="price">$950 per week</p>
          </div>
        </div>
      </li> -->
    </ul>
    <footer class="realEstate_footer">
      <ui-button :disabled="!selectedProperty" unelevated>Select Property</ui-button>
      <!-- <button  class="realEstate_btn">Select Property</button> -->
    </footer>
  </section>
</template>

<script>
import jsonData from "@/data/data.json";
export default {
  data() {
    return {
      selectedProperty: null,
    };
  },
  computed: {
    myJson() {
      return jsonData;
    },
  },
};
console.log(jsonData);
</script>

<style scoped>
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
  font-family: "Rubik";
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
  font-family: "Rubik";
  font-style: normal;
  font-weight: 500;
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
