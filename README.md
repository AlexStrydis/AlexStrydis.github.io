<html lang="en">
<head>
<meta charset="UTF-8">
<link rel="shortcut icon" type="image/x-icon" href="https://static.codepen.io/assets/favicon/favicon-aec34940fbc1a6e787974dcd360f2c6b63348d4b1f4e06c77743096d55480f33.ico" />
<link rel="mask-icon" type="" href="https://static.codepen.io/assets/favicon/logo-pin-8f3771b1072e3c38bd662872f6b673a722f4b3ca2421637d5596661b4e2132cc.svg" color="#111" />
<title>CodePen - Spacy 404 with count up</title>
<link rel='stylesheet' href='https://cdn.3up.dk/flexgrid.io@2.5.1/css/flexgrid.min.css'>
<style>
    @import url("https://fonts.googleapis.com/css?family=Roboto+Mono:300,500");
html, body {
  width: 100%;
  height: 100%;
}

body {
  background-image: url(https://s3-us-west-2.amazonaws.com/s.cdpn.io/257418/andy-holmes-698828-unsplash.jpg);
  background-size: cover;
  background-repeat: no-repeat;
  min-height: 100vh;
  min-width: 100vw;
  font-family: "Roboto Mono", "Liberation Mono", Consolas, monospace;
  color: rgba(255, 255, 255, 0.87);
}

.mx-auto {
  margin-left: auto;
  margin-right: auto;
}

.container,
.container > .row,
.container > .row > div {
  height: 100%;
}

#countUp {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100%;
}
#countUp .number {
  font-size: 4rem;
  font-weight: 500;
}
#countUp .number + .text {
  margin: 0 0 1rem;
}
#countUp .text {
  font-weight: 300;
  text-align: center;
}

  </style>
<script>
  window.console = window.console || function(t) {};
</script>
<script>
  if (document.location.search.match(/type=embed/gi)) {
    window.parent.postMessage("resize", "*");
  }
</script>
</head>
<body translate="no">

<div class="container">
<div class="row">
<div class="xs-12 md-6 mx-auto">
<div id="countUp">
<div class="number" data-count="404">0</div>
<div class="text">Page not found</div>
<div class="text">This may not mean anything.</div>
<div class="text">I'm probably working on something that has blown up.</div>
</div>
</div>
</div>
</div>
<script src="https://static.codepen.io/assets/common/stopExecutionOnTimeout-de7e2ef6bfefd24b79a3f68b414b87b8db5b08439cac3f1012092b2290c719cd.js"></script>
<script src='https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js'></script>
<script src='https://cdn.3up.dk/in-view@0.6.1'></script>
<script id="rendered-js">
      var formatThousandsNoRounding = function (n, dp) {
  var e = '',s = e + n,l = s.length,b = n < 0 ? 1 : 0,
  i = s.lastIndexOf(','),j = i == -1 ? l : i,
  r = e,d = s.substr(j + 1, dp);
  while ((j -= 3) > b) {if (window.CP.shouldStopExecution(0)) break;r = '.' + s.substr(j, 3) + r;}window.CP.exitedLoop(0);
  return s.substr(0, j + 3) + r + (
  dp ? ',' + d + (d.length < dp ?
  '00000'.substr(0, dp - d.length) : e) : e);
};

var hasRun = false;

inView('#countUp').on('enter', function () {
  if (hasRun == false) {
    $('.number').each(function () {
      var $this = $(this),
      countTo = $this.attr('data-count');

      $({ countNum: $this.text() }).animate({
        countNum: countTo },

      {
        duration: 2000,
        easing: 'linear',
        step: function () {
          $this.text(formatThousandsNoRounding(Math.floor(this.countNum)));
        },
        complete: function () {
          $this.text(formatThousandsNoRounding(this.countNum));
        } });

    });
    hasRun = true;
  }
});
      //# sourceURL=pen.js
    </script>
</body>
</html>

