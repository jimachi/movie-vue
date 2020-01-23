<template>
  <div>
    <nav>
      <ul>
        <li class="logo" ><a href="#">TOP</a></li>
        <li class="nav-menu" ><a href="#">New</a></li>
        <li class="nav-menu"><a href="#">Contact</a></li>
        <li class="nav-menu"><a href="#">About</a></li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  
}
</script>

<style lang="scss" scoped>
ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
    background: #333333;
    li {
      float: left;
      a {
        display: block;
        color: #ffffff;
        text-align: center;
        padding: 14px 16px;
        text-decoration: none;
      }
    }
}
</style>