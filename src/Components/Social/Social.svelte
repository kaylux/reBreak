<script>
  export let socialData = {};
  const { IMAGES_LIST, HEADING } = socialData;
</script>
<!------------------------------------------->
<!----------------MARKUP----------------------->
<!------------------------------------------->
<section id="social-media" class="section grey-bgcolor">
  <div class="container text-center">
    <h2 class="title text-center">{HEADING}</h2>
    <div class="social-icons section-body">
    

      <a href="https://www.facebook.com/rebreaknews/"
          target="_blank">
          <img src={IMAGES_LIST[0]} alt="Social media {IMAGES_LIST[0]}" />

      </a>
        <a href="https://www.instagram.com/rebreaknews/"
          target="_blank">
          <img src={IMAGES_LIST[1]} alt="Social media {IMAGES_LIST[1]}" />
      </a>
        <a href="https://www.twitter.com/rebreaknews/"
          target="_blank">
          <img src={IMAGES_LIST[2]} alt="Social media {IMAGES_LIST[2]}" />
      </a>
     

    </div>
  
  </div>
</section>
<!------------------------------------------->
<!----------------STYLE----------------------->
<!------------------------------------------->
<style>
  .social-icons img {
    width: 75px;
    transition: 0.5s;
  }
  .social-icons a:hover img {
    transform: translateY(-10px);
  }
  a:hover {
    text-decoration: none;
  }
</style>