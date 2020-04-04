<script>
  export let videoData = {};
  const { HEADING, HEADING2, SERVICE_LIST, MAINVID } = videoData;

  import  { onMount  } from "svelte";
  import lazySizes from 'lazysizes';
import 'lazysizes/plugins/attrchange/ls.attrchange';

  var key = 'AIzaSyC5UTeickpgiE_xSIXJqDZXMZ5rzq9Ty00';
  var url = 'https://www.googleapis.com/youtube/v3/channels';
  var channelid = 'UCwIxn6d5t7gZvebnGUoWJ3A';
  var mainVideo;
  var data;
  var data2;//most popular
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


  var options = {
    part: "snippet",
    key: key,
    id: channelid,
    maxresults: 20

  };
  function changeHandler() {

    if(videoSelection == 0){
            videoSelection = "1";
      HeadingText = "MOST POPULAR";
          for(var index = 0; index < data.items.length; index++){
        vids3[index] = data2.items[index].id.videoId; 
    
   }
    console.log(vids3);
    console.log(displayedvids);

    
      for(var index = 0; index < data2.items.length; index++){
     
      
        displayedvids = vids3;
        console.log(displayedvids);
        
   
      }


    }
    if(videoSelection == 1){
      
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
    const response = await fetch('https://www.googleapis.com/youtube/v3/search?part=snippet&type=video&key=AIzaSyC5UTeickpgiE_xSIXJqDZXMZ5rzq9Ty00&maxResults=25&channelId=UCwIxn6d5t7gZvebnGUoWJ3A&order=date');
      
    const response2 = await fetch('https://www.googleapis.com/youtube/v3/search?part=snippet&type=video&key=AIzaSyC5UTeickpgiE_xSIXJqDZXMZ5rzq9Ty00&maxResults=25&channelId=UCwIxn6d5t7gZvebnGUoWJ3A&order=viewcount');
    data = await response.json();
    data2 = await response2.json();
    console.log(data);
    console.log(data2);
   

    mainVideo = MAINVID;
  
    
    for(var index = 0; index < data.items.length; index++){
        vids[index] = data.items[index].id.videoId; 
    
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

  <div class="container text-center">
        <h2 class="title">{HEADING2}</h2>
    
     <iframe class="mainvid" width="400" height="340"
             data-src="https://www.youtube.com/embed/Fts0R_SkKnI">
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

         <iframe class='youtubebox' width="320" height="200"
            src="https://www.youtube.com/embed/{vid}">
         </iframe>
   
      
      {/each}
      
      </div>
</section>
<!------------------------------------------->
<!----------------STYLE----------------------->
<!------------------------------------------->
<style>

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
</style>