![alt text](https://www.mv.helsinki.fi/home/asahala/img/babyfst.png)

Babylonian Finite-State Morphology v. 2.0

<textarea id="input-data" style="width: 100%" rows="5" placeholder="Try this input:
šarru
kaspam
iddin" autofocus></textarea>
<pre id="output-data" style="margin-top: 1em"></pre>
<script src="babyfst.js"></script>
<script src="foma_apply_down.js"></script>
<script>
var
  inputTimeout = 500 /* ms */,
  inputData = document.getElementById('input-data'),
  outputData = document.getElementById('output-data'),
  delay = function(callback, ms) { // SO:1909441
    var timer = 0;
    return function() {
      var context = this;
      var args = arguments;
      clearTimeout(timer);
      timer = setTimeout(function() {
        callback.apply(context, args);
      }, ms || 0);
    };
  };
inputData.addEventListener('input', delay(function(event) {
  var input = inputData.value;
  if (input === '') {
    outputData.textContent = '';
  } else {
    outputData.textContent = input.split('\n').map(function(line) {
      return '' + foma_apply_down(BabyFST, line);
    }).join('\n');
  }
}, inputTimeout));
</script>


# Main repository

The main repository of this project is <a href="https://github.com/asahala/BabyFST">asahala/BabyFST</a>
