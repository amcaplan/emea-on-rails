---
layout: post
title: Secret Uploads - shhhhhh! 🤫
noindex: true
---

<button id="upload_widget" class="cloudinary-button">Upload files</button>

<script src="https://upload-widget.cloudinary.com/global/all.js" type="text/javascript"></script>  

<script type="text/javascript">  
(function() {
  var myWidget = cloudinary.createUploadWidget({
    cloudName: 'emea-on-rails',
    uploadPreset: 'emea-on-rails-2021-featured-videos'}, (error, result) => {
      if (!error && result && result.event === "success") {
        console.log('Done! Here is the video info: ', result.info);
      }
    }
  )

  var button = document.getElementById("upload_widget");
  button.addEventListener("click", function(){
    myWidget.open();
  }, false);
  button.click();
})();
</script>
