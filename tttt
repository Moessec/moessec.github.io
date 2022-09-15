
  // Initialize the agent at application startup.
  const fpPromise = import('https://openfpcdn.io/fingerprintjs/v3')
    .then(FingerprintJS => FingerprintJS.load())
  // Get the visitor identifier when you need it.
  fpPromise
    .then(fp => fp.get())
    .then(result => {
      const visitorId = result.visitorId
      console.log(visitorId)
      const device_id = getCookie("device_id");
      if (device_id != "") {
          if (device_id != visitorId ){
              setCookie("device_id", visitorId)
          }
       } else
       {
         setCookie("device_id", visitorId, 365)
       }
    })

  function setCookie(cname,cvalue,exdays)
   {
    const d = new Date();
    d.setTime(d.getTime()+(exdays*24*60*60*1000));
    const expires = "expires="+d.toGMTString();
    document.cookie = cname + "=" + cvalue + "; " + expires + "; path=\/;";
  }
  function getCookie(user) {
    const cookieArr = document.cookie.split(";");
    for(i = 0; i < cookieArr.length; i++) {
        const cookiePair = cookieArr[i].split("=");
        if(user == cookiePair[0].trim()) {
            return decodeURIComponent(cookiePair[1]);
        }
    }
    return null;
}
