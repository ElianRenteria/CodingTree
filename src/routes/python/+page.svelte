<script>
  import Sk from "skulpt";

  let code = ``; // Default code

  let testCases = [
    { input: "add(2, 3)", expected: "5" },
    { input: "add(10, 20)", expected: "30" },
  ];

  let output = "";

  function runPython() {
    output = ""; // Clear previous output

    function outf(text) {
      output += text; // Capture output
    }

    function builtinRead(x) {
      if (!Sk.builtinFiles || !Sk.builtinFiles["files"][x]) {
        throw "File not found: '" + x + "'";
      }
      return Sk.builtinFiles["files"][x];
    }

    Sk.configure({ output: outf, read: builtinRead, execLimit: 1000});

    let userCode = code + "\n\n";
    let testResults = "";

    // Ensure output for test cases is captured separately
    let testOutputs = [];
    for (let test of testCases) {
      userCode += `print(repr(${test.input}))\n`; // Ensure consistent string output
      testOutputs.push(test.expected);
    }

    Sk.misceval
      .asyncToPromise(() => Sk.importMainWithBody("<stdin>", false, userCode))
      .then(() => {
        let results = output.trim().split("\n");
        for (let i = 0; i < testCases.length; i++) {
          let expected = testCases[i].expected.trim();
          let actual = results[i] ? results[i].trim() : "undefined";

          if (actual === expected) {
            testResults += `✅ Test ${i + 1} passed\n`;
          } else {
            testResults += `❌ Test ${i + 1} failed\n  Input: ${testCases[i].input}\n  Expected: ${expected}\n  Got: ${actual}\n`;
          }
        }
        output = testResults;
      })
      .catch((err) => {
        output = err.toString().includes("TimeLimitError")
          ? "Error: Execution time limit exceeded.\nPlease check your code for infinite loops."
          : "Error: " + err.toString();
      });
  }

</script>

<div class="container-fluid">
  <div class="header">
    <h1>Python Code Editor</h1>
    <div class="content">
      <div class="col">
        <textarea bind:value={code} rows="10" cols="50"></textarea>
        <button on:click={runPython}>Run Code</button>
      </div>
      <div class="output">
        <pre>{output}</pre>
      </div>
    </div>
  </div>
</div>
<style>
  .col {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-top: .5rem;
  }
  textarea {
    width: 100%;
    max-width: 25rem;
    font-family: monospace;
  }
  button {
    margin: 1rem 0;
    padding: 0.5rem 1rem;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  pre {
    background: #f4f4f4;
    padding: 1rem;
    border-radius: 5px;
    white-space: pre-wrap;
    width: 100%;
    max-width: 25rem;
  }
  .content {
    display: flex;
    justify-content: center;
    align-items: start;
    width: 100%;
    gap: 1rem;
  }
  .output {
    margin-top: .5rem;
    width: 100%;
    max-width: 25rem;
  }
  .header {
    margin-top: 1rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
  }
  h1 {
    font-weight: 500;
    color: rgb(101, 101, 101);
  }
</style>
