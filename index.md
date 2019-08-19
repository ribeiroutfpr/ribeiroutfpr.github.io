<html lang="pt-br">

<body>
    <h1>Meu primeiro Podcast.</h1>
    
    <style>
  #videogroup {
    width: 100%;
  }

 iframe {
    width: 90%;
    padding: 5%;
  }

  #myplayer .first iframe {
    width: 100%;
    padding: 0;
  }
  
  #videolist ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  #videolist li {
    width: 50%;
    float: left;
    border: none;
    position: relative;
  }

  #videolist li .entriestitle {
    padding: 0 5px;
    position: absolute;
    left:80%;
    top:20%;
    display: none;
  }
  
  #videolist li:hover .entriestitle {
    display: block;
    width: 100%;
    background: rgb(119, 25, 51);
    border-radius: 10px;
    color: #FFF;
    padding: 10px;
    opacity: .9;
    z-index: 100;
    right: 0;
  }

</style>

<script type="text/javascript">

function listVideos(data) {
  var firstOutput="";
  var entries = data.feed.entry;
  var myOutput = '<ul>';
  for (var i=0; i<data.feed.entry.length; i++) {
    var entriesID=entries[i].id.$t.substring(38);
    var entriesTitle=entries[i].title.$t;
    var entriesDescription=entries[i].media$group.media$description.$t;
    var entriesThumbnail=entries[i].media$group.media$thumbnail[0].url;
    myOutput += '<li><div class="entriestitle">' + entriesTitle + '</div>';
    myOutput+='<iframe src="http://www.youtube.com/embed/'+entriesID+'?wmode=transparent&amp;HD=0&amp;rel=0&amp;showinfo=0&amp;controls=1&amp;fs=1&amp;autoplay="0" frameborder="0" allowfullscreen></iframe>';
    if (i==0) {
      firstOutput += '<div class="first">';
      firstOutput += '<h2>' + entriesTitle + '</h2>';
      firstOutput += '<iframe src="http://www.youtube.com/embed/'+entriesID+'?wmode=transparent&amp;HD=0&amp;rel=0&amp;showinfo=0&amp;controls=1&amp;autoplay="0" frameborder="0" allowfullscreen></iframe>';
      firstOutput += '<p>' + entriesDescription + '</p>';
      firstOutput += '</div>';
      document.getElementById('myplayer').innerHTML=firstOutput;
    }
  }
  document.getElementById('videolist').innerHTML = myOutput;
  myOutput +='</ul>';
}
</script>

<div id="videogroup">
  <div id="myplayer"></div>
  <div id="videolist"></div>
</div>

<script type="text/javascript" src="https://www.youtube.com/watch?v=Of5A6o9J_F8?alt=json-in-script&callback=listVideos&max-results=6&category=Villalobos"></script>

    
    <p>Agradecimentos especiais à Enigma Pistolinha</p>
</body>
</html>
