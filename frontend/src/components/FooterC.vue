<template>
  <footer class="footer">
    <div class="container">
      <div class="row">
        <div class="col-md-6">
          <h5>About Me</h5>
          <ul>
            <li><a href="#">My Story</a></li>
            <li><a href="#">Contact Me</a></li>
          </ul>
        </div>

        <div class="col-md-6">
          <h5>Follow Me</h5>
          <ul>
            <li><a href="#">Facebook</a></li>
            <li><a href="#">Twitter</a></li>
            <li><a href="#">Instagram</a></li>
          </ul>
        </div>
      </div>
      <hr>
      <div class="row">
        <div class="col-12">
          <p>&copy; 2023 Archie-Vable Gaming. All rights reserved.</p>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default{
  name: 'footer-'
}
</script>

<style scoped>
.footer{
  background-color: #2e2c2c;
  padding: 50px 0;
  text-align: center;
}

.footer h5{
  color: #fff;
  font-size: 18px;
  margin-bottom: 25px;
}

.footer ul li a{
  color: #fff;
  font-size: 14px;
  line-height: 24px;
}

.footer hr{
  border-color: #fff;
  margin: 40px 0;
}

.footer p{
  color: grey;
  font-size: 14px;
  line-height: 24px;
}
</style>

  