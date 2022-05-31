<template>
  <section class="welcome_screen">
    <div class="title">
      <h1 class="first_title">Lorem</h1>
      <h1 class="second_title">Ipsum</h1>
    </div>
    <div class="paragraph">
      <p>
        Lorem Ipsum is simply dummy text of the printing and typesetting
        industry. Lorem Ipsum has been the industry's standard dummy text ever
        since the 1500s, when an unknown printer took a galley of type and
        scrambled it to make a type specimen book.It has survived not only five
        centuries, but also the leap into electronic typesetting, remaining
        essentially unchanged.
      </p>
      <p>
        It was popularised in the 1960s with the release of Letraset sheets
        containing Lorem Ipsum passages, and more recently with desktop
        publishing software like Aldus PageMaker including versions of Lorem
        Ipsum.
      </p>
    </div>
    <div class="footer">
      <button @click="$emit('startQuiz')" class="button_start">
        Start Quiz
      </button>
    </div>
  </section>
</template>

<script></script>

<style>
.title {
  display: flex;
  position: absolute;
  top: 81px;
  left: 50%;
  transform: translateX(-50%);
}
.first_title {
  font-family: "Nunito";
  font-weight: 400;
  font-size: 36px;
  line-height: 43.2px;
}
.second_title {
  font-family: "Nunito";
  font-weight: 700;
  font-size: 36px;
  line-height: 43.2px;
}
p {
  padding: 0 56px 20px 56px;
  font-family: "Nunito";
  font-weight: 400;
  font-size: 16px;
  line-height: 25.6px;
}
.paragraph {
  position: relative;
  top: 200px;
  left: 50%;
  transform: translateX(-50%);
}
.footer {
  display: flex;
  justify-content: center;
  width: 100%;
  background: #000000;
  box-shadow: 0px -5px 50px rgba(15, 26, 66, 0.05);
  border-radius: 20px;
  position: absolute;
  bottom: 0;
  height: 70px;
  align-items: center;
}
.button_start {
  background: #ffffff;
  border-radius: 10px;
  height: 40px;
  width: 178px;
  cursor: pointer;
}
</style>
