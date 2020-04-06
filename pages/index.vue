<template>
  <div class="background">
    <div class="container">
      <div class="TitleInfo">
        <!-- <logo /> -->
        <h1 class="title">
          Noah Mushkin
        </h1>
        <h2 class="subtitle">
          Web Portfolio
        </h2>
        <p class="p-content">
          I am a computer science major at Dartmouth College who enjoys building
          with code, wood, metal and any other materials I can get my hands on.
          Welcome to my homepage, where you can find out more about what I've
          built and what I'm working on now.
        </p>
        <div class="links">
          <a
            href="https://github.com/nmushkin"
            target="_blank"
            class="button--white"
          >
            GitHub
          </a>
          <a
            href="https://portnm.s3-us-west-1.amazonaws.com/NoahMushkinResume.pdf"
            target="_blank"
            class="button--white"
          >
            Résumé
          </a>
        </div>
      </div>
    </div>
    <p>(This image comes from my stock market art project)</p>
  </div>
</template>

<script></script>

<style scoped>
.TitleInfo {
  background-color: rgba(100, 100, 100, 0.8);
  padding: 15px;
  border-radius: 4px;
}
.background {
  background-image: url('~static/bgimage2.png');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center fixed;
  height: 94vh;
  text-align: center;
}
.container {
  margin: 0 auto;
  min-height: 88vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.links {
  padding-top: 15px;
}
</style>
