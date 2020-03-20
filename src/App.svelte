<script>
  import Navbar from "./Components/Navbar/Navbar.svelte";
  import Banner from "./Components/Banner/Banner.svelte";
  import Services from "./Components/Services/Videos.svelte";

 
  import Social from "./Components/Social/Social.svelte";
  import Footer from "./Components/Footer/Footer.svelte";

  import DATA from "./Data/data";
  console.log(DATA);
</script>

<!-- Navbar -->
<Navbar navlists={DATA.NAVBAR_DATA} header={DATA.HEADER} /> 
<!-- Banner -->
<Banner bannerData={DATA.BANNER_DATA} } />
<!-- Youtube Data -->

<!-- Videos -->
<Services videoData={DATA.VIDEO_DATA} />

<!-- Social Media -->
<Social socialData={DATA.SOCIAL_DATA} />

<!-- Footer -->
<Footer footerData={DATA.FOOTER_DATA} header={DATA.HEADER} />
