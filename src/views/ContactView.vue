<template>
  <head>
    <link href="https://cdn.jsdelivr.net/npm/boxicons@latest/css/boxicons.min.css" rel="stylesheet">
  </head>
  <div class="container">
          <div class="row">
            <div class="col-md-4 pr-md-5">
              <a href="#" class="footer-logo d-block mb-4">Coffee4You</a>
              <p>Restauracja Dobry Smak, ul.Szeroka&nbsp;22, Szczebrzeszyn, Polska</p>
            </div>
           
            <div class="col-md text-md-center">
              <ul class="social list-unstyled">
                <li><a href="mailto:mail@mail.com"><span class="bx bx-mail-send"></span></a></li>
                <li><a href="https://www.instagram.com/wyzsze_szkoly_bankowe/" target="_blank"><span class="bx bxl-instagram"></span></a></li>
                <li><a href="https://www.youtube.com/user/GrupaWSB" target="_blank"><span class="bx bxl-youtube"></span></a></li>
                <li><a href="https://twitter.com/eksperci_wsb" target="_blank"><span class="bx bxl-twitter"></span></a></li>
                <li><a href="https://www.facebook.com/WSBgdansk/" target="_blank"><span class="bx bxl-facebook"></span></a></li>
              </ul>
              <p>Contact Us</p>
            </div>
          </div> 
  
        </div>
</template>

<script>

export default {
  name: "ContactView"
}
</script>

<style scoped>
.social li {
    display: inline-block;
}

.social a {
    color: black;
    padding: 7px;
    font-size: 1.5rem;
}

.social a:hover {
    color: blue;
    border: 2px solid blue;
    border-radius: 50%;
}

.social a:focus {
    color: black;
    border: 0px;
}

</style>