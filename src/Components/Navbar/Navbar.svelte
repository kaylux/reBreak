<script>
  export let navlists = [];
  export let header;
  
  let active = false;
  export let videoData = {};
  const { HEADING, HEADING2, SERVICE_LIST, MAINVID } = videoData;

 


</script>
<button on:click={()=> active = !active}>
	{active? 'Close' : 'Open'} Menu
</button>

<aside class:active>
	    <div id="sidebar-wrapper">
      <ul class="sidebar-nav">
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
    </div>
</aside>


<style>
	aside {
		position: absolute;
		left: -500px;
		transition: all .5s;
		height: 500px;
		width: 300px;
		padding: 20px;
		border: 1px solid #ddd;
		background-color: #efefef;
             z-index: 10;
	}
	.active {
		left: 0px
	}
/* Sidebar styling */
.sidebar-nav{
  padding:0;
  list-style:none; 
	transition:all .5s;
	width:100%;
	text-align:center;
}

.sidebar-nav li{
  line-height:40px;  
	width:100%;
	transition:all .3s;
	padding:10px;
}

.sidebar-nav li a {
  display:block;
  text-decoration:none;
  color:rgb(255, 0, 0);
}

.sidebar-nav li:hover{
  background:#846bab;

}
.sidebar-nav li:hover a{
	color:white;

}


 


</style>