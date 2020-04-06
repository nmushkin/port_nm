<template>
  <div>
    <NavBar />
    <nuxt />
  </div>
</template>

<script>
import NavBar from '~/components/NavBar'

export default {
  components: {
    NavBar
  }
}
</script>

<style>
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  /* background-color: #aaaaaa; */
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}

.button--white {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #bbbbbb;
  color: #bbbbbb;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--white:hover {
  color: #fff;
  background-color: #aaaaaa;
}

.button--nav {
  display: inline-block;
  border-radius: 4px;
  /* border: 1px solid #dddddd; */
  color: #dddddd;
  text-decoration: none;
  padding: 10px 30px;
  margin: 5px;
}

.button--nav:hover {
  color: #fff;
  /* background-color: #666666; */
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 80px;
  color: #cccccc;
  letter-spacing: 1px;
}

.title-dark {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 80px;
  color: #444444;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 34px;
  color: #bbbbbb;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.subtitle-dark {
  font-weight: 300;
  font-size: 34px;
  color: #555555;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.p-content {
  color: #aaaaaa;
}
</style>
