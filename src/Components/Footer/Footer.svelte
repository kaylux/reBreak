<script>
  export let footerData = {};
  export let header = "";
  const {
    DESCRIPTION,
    CONTACT_DETAILS,
    SUBSCRIBE_NEWSLETTER,
    SUBSCRIBE
  } = footerData;
  const { HEADING, ADDRESS, MOBILE, EMAIL } = CONTACT_DETAILS;
</script>

<!------------------------------------------->
<!----------------MARKUP----------------------->
<!------------------------------------------->
<section class="main-bgcolor light-color" id="footer">
 
  <div class="container">
    <div class="row section-body">
      <div class="col-md-4 footer-box center">
        <div class="company_brand">{header}</div>
        <p> Keeping you in the loop</p>
      </div>
    </div>
  </div>
</section>
<!------------------------------------------->
<!----------------Style----------------------->
<!------------------------------------------->
<style>
  .footer-title {
    font-weight: bold;
    text-transform: uppercase;
  }

  .footer-box button {
    margin-top: 30px;
  }

  .round-border {
    border-radius: 20px !important;
  }
  .wave-img {
    width: 100%;
    height: auto;
  }
</style>