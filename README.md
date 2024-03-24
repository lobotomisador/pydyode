# README
Run the scientific python stack in the browser (https://pyodide.org/en/stable/)

This allows browsers to do linear algebra by leveraging BLAS/LAPACK, offloading the work to the client's device.

# Quickstart.
Load the pyodide script.
```
    <script src="https://cdn.jsdelivr.net/pyodide/v0.20.0/full/pyodide.js"></script>
    <script type="text/javascript">
      let pydiode
      async function main(){
        pyodide = await loadPyodide()
        await pyodide.loadPackage("numpy")
        console.log(pyodide.runPython(`
            import sys
            import numpy
            sys.version
       `))
        console.log(pyodide.runPython("print(1 + 2)"))
      }
      main()
      const runPython = s => console.log(pyodide.runPython('sum([1,2,5])'))
      runPython()
    </script>
```

Then load scientific python packages with  `await pyodide.loadPackage("numpy")`, then just call `pyodide.runPython(...)` with your favorite function.
