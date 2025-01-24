<div id="content">
    <iframe title="code" src="https://trinket.io/embed/python3" width="100%" height="100%" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>
    <!--<h3>Try This</h3>
    <button type="button" on:click={runit}>Run</button> 
    <div id="code_container">
        <form> 
        <textarea id="yourcode" cols="40" rows="10">print("Hello World")</textarea>
        </form> 
        <h6>Output</h6>
        <pre id="output" ></pre>
    </div>  
    <div id="mycanvas"></div> -->
</div>


<script type="text/javascript">
    import Sk from 'skulpt';
    import 'jquery'
    // This function ensures that Skulpt is ready before running any code
    function runit() {
        var prog = document.getElementById("yourcode").value; 
        var mypre = document.getElementById("output"); 
        mypre.innerHTML = ''; 
        Sk.pre = "output";
        Sk.configure({output:outf, read:builtinRead}); 
        (Sk.TurtleGraphics || (Sk.TurtleGraphics = {})).target = 'mycanvas';
        Sk.externalLibraries = {
            requests: {
                path: 'static/'
            }
        }
        var myPromise = Sk.misceval.asyncToPromise(function() {
            return Sk.importMainWithBody("<stdin>", false, prog, true);
        });
        myPromise.then(function(mod) {
            console.log('success');
        },
            function(err) {
            console.log(err.toString());
        });
    }

    function outf(text) { 
        var mypre = document.getElementById("output"); 
        mypre.innerHTML = mypre.innerHTML + text; 
    } 

    function builtinRead(x) {
        if (Sk.builtinFiles === undefined || Sk.builtinFiles["files"][x] === undefined)
            throw "File not found: '" + x + "'";
        return Sk.builtinFiles["files"][x];
    }
</script>

<style>
    #mycanvas {
        border: 1px solid black;
        width: 500px;
        height: 500px;
    }
    #content{
        width: 100%;
        height: 90vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: start;
    }
    #yourcode{
        text-align: left;
    }
    #mycanvas{
        display: none;
    }
    #output{
        text-align: left;
        width: 100%;
        border: 1px solid rgba(0, 0, 0, 0.484);
        padding: .3rem;
        border-radius: .2rem;
    }
    h6{
        color: grey;
        margin: 0;
        margin-top: 1rem;
        padding: 0;
    }
    #code_container{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: start;
    }
</style>