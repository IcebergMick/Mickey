// Function to check if the browser supports the MediaDevices API
function isMediaDevicesSupported() {
  return !!(navigator.mediaDevices && navigator.mediaDevices.getUserMedia);
}

// Function to request permission for accessing media songs
function requestMediaPermission() {
  if (isMediaDevicesSupported()) {
    navigator.mediaDevices.getUserMedia({ audio: true })
      .then(function(stream) {
        // Permission granted, handle the stream or perform further actions
        console.log("Permission granted");
      })
      .catch(function(error) {
        // Permission denied or error occurred
        console.log("Permission denied or error occurred:", error);
      });
  } else {
    console.log("MediaDevices API is not supported in this browser.");
  }
}

// Call the function to request permission when a button is clicked or any other event
document.getElementById("requestPermissionButton").addEventListener("click", requestMediaPermission);
