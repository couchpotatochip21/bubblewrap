<main>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <!-- repeat -->
</main>
<style>
  main {
    display: flex;
    flex-flow: column row;
  }
  main > div {
    height: 50px;
    width: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50px;
    margin: 12px;
    border: solid 4px black;
    transition: border-radius 1s ease-in, border 0.5s ease;  
  }
  main > .popped {
    border-radius: 0;
    border: none;
  }
</style>
<script>
let blob = undefined;
document.querySelectorAll("main > div").forEach(b => b.addEventListener("click", _ => {b.classList.add("popped"); b.innerHTML = '<div>*pop*</div>'; !blob ? null : new Audio(blob).play();}));
var xhr = new XMLHttpRequest();
    xhr.open('GET', 'pop.mp3', true);
    xhr.responseType = 'blob'; //important
    xhr.onload = function(e) {
        if (this.status == 200) {
            var Blob = this.response;
            blob = URL.createObjectURL(Blob);
        }
    };
    xhr.send();
</script>
