<script>
  export let videoData = {};
  const { HEADING, HEADING2, SERVICE_LIST, MAINVID, data, data2 } = videoData;

  import  { onMount  } from "svelte";

  var channelid = 'UCwIxn6d5t7gZvebnGUoWJ3A';
  var vid1;
  var displayedvids = [ ];
  var vids = [ ];
  var vids2 = [ ];
  var vids3 = [ ];
  var vids4 = [ ]; 
  var vidNames = [ ];
  var videoSelection = 0;
  var HeadingText = "LATEST VIDEOS";


 console.log(HEADING2);




  document.addEventListener('lazybeforeunveil', function(e){
    console.log("lazy load init");
});
  function changeHandler() {

 
    if(videoSelection == 0){
            videoSelection = "1";
      HeadingText = "MOST POPULAR";

      for(var index = 0; index < 20; index++){
    
        if(data2.items[index].id.kind == 'youtube#channel'){


          displayedvids = vids4;
   
    
        }
      }


    }
    if(videoSelection == 1){
      videoSelection = 0;
      HeadingText = "LATEST VIDEOS";
      for(var index = 0; index < 20; index++){
      
        displayedvids = vids2;
      

      }
      videoSelection = "0";
    }

    document.querySelectorAll('.youtubebox').forEach(function(iframe) {
    iframe.contentWindow.location.reload();
});
  }



  onMount(async function(){
    const response = await fetch('https://www.googleapis.com/youtube/v3/search?order=date&part=id&channelId=UCwIxn6d5t7gZvebnGUoWJ3A&maxResults=15&key=AIzaSyA-9s61JkXwiAuZE3yGSULCFJGzQIiJktQ');
  
    const response2 = await fetch('https://www.googleapis.com/youtube/v3/search?part=id&channelId=UCwIxn6d5t7gZvebnGUoWJ3A&key=AIzaSyA-9s61JkXwiAuZE3yGSULCFJGzQIiJktQ&maxResults=15&order=viewcount');
    data = await response.json();
    data2 = await response2.json();
    console.log(data);
    console.log(data2);
   
    
    for(var index = 0; index < 15; index++){
        vids[index] = data.items[index].id.videoId;
        vids3[index] = data2.items[index].id.videoId;
     
   }
  



vids2 = vids.filter(function(x){
     return x !== undefined;


   });
   vids4 = vids3.filter(function(x){
     return x !== undefined;


   });
   console.log(vids2);
   displayedvids = vids2;
   console.log(vids4);

   
   

  
  });




      
</script>

<!------------------------------------------->
<!----------------MARKUP----------------------->
<!------------------------------------------->
<section id="services" class="section">

    <div class="facebooklike ">

      <iframe src="https://www.facebook.com/plugins/like.php?href=https%3A%2F%2Fwww.facebook.com%2Frebreaknews&width=450&layout=standard&action=like&size=small&share=true&height=35&appId=778425398911705" width="450" height="35" style="border:none;overflow:hidden" scrolling="no" frameborder="0" allowTransparency="true" allow="encrypted-media"></iframe>
    </div>
  <div class="container text-center">
        <h2 class="title">{HEADING2}</h2>
    
     <iframe class="lazyload" width="400" height="340"
             data-src="https://www.youtube.com/embed/{MAINVID}">
          </iframe>
    <br><br><br>



    <h2 class="title">{HeadingText}</h2>
    <label class="switch">
  <input type="checkbox" on:change={changeHandler}>
  <span class="slider round"></span>
</label>
    <div class="row section-body">
     
        

      <div class="youtubebox">
      {#each displayedvids as vid}

      

        <iframe class='lazyload' width="320" height="200"
            data-src="https://www.youtube.com/embed/{vid}">
         </iframe>
   
    
      
      {/each}
      
      </div>
</section>
<!------------------------------------------->
<!----------------STYLE----------------------->
<!------------------------------------------->
<style>

  .facebooklike{
    display:flex;
  }
  .facebooklike iframe{
    margin-left: auto;
    margin-right: auto;
    justify-content: center; 
  }



  .service-img {
    width: 200px;
    height: 200px;
    margin-top: 20px;
  }

  .service h4 {
    padding: 5px;
    margin-top: 25px;
    text-transform: uppercase;
  }

  .title {
    text-transform: uppercase;
  }

  .title::before {
    content: "";
    background: linear-gradient(90deg, #c72c2c 0%, #ff0000 100%);
    height: 5px;
    width: 200px;
    margin-left: auto;
    margin-right: auto;
    display: block;
    transform: translateY(60px);
  }

  .title::after {
    content: "";
    background: linear-gradient(90deg,#f11818 0%, #a53a3a 100%);
    height: 10px;
    width: 50px;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 40px;
    display: block;
    transform: translateY(14px);
  }

  section .btn-primary {
    box-shadow: none;
    padding: 8px 25px;
    border: none;
  }

  /* The switch - the box around the slider */
.switch {
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
}

/* Hide default HTML checkbox */
.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

/* The slider */
.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: .4s;
  transition: .4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: .4s;
  transition: .4s;
}

input:checked + .slider {
  background-color: #2196F3;
}

input:focus + .slider {
  box-shadow: 0 0 1px #2196F3;
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

/* Rounded sliders */
.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}

.youtubebox{


  object-fit: contain;
}
.youtube {
 
    width: 300px;
    height: 200px;
    background-color: #000;
    object-fit: contain;
    position: relative;
  
    overflow: hidden;
    cursor: pointer;
}
.youtube img {
   
   object-fit: contain;
    left: 0;
    opacity: 0.7;
}
.youtube .play-button {
    width: 90px;
    height: 60px;
    background-color: #333;
    box-shadow: 0 0 30px rgba( 0,0,0,0.6 );
    z-index: 1;
    opacity: 0.8;
    border-radius: 6px;
}
.youtube .play-button:before {
    content: "";
    border-style: solid;
    border-width: 15px 0 15px 26.0px;
    border-color: transparent transparent transparent #fff;
}
.youtube img,
.youtube .play-button {
    cursor: pointer;
}
.youtube img,
.youtube iframe,
.youtube .play-button,
.youtube .play-button:before {
    position: absolute;
}
.youtube .play-button,
.youtube .play-button:before {
    top: 50%;
    left: 50%;
    transform: translate3d( -50%, -50%, 0 );
}
.youtube iframe {
    height: 100%;
    width: 100%;
    top: 0;
    left: 0;
}
</style>