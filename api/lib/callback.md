# lib.Callback

Construct and chain callbacks.

## Class: lib.Callback

### new lib.Callback ()

### cb.run (fn)
1. `fn {function}`
2. Return: `{this}`

Add a callback function to the list of callbacks.

### cb.run (thisObj, method)
1. `thisObj {object}` 
2. `method {string}`
3. Return: `{this}`

Add a callback to the callback chain by specifying the
object and the method to call within that object. If
callback has fired, run it straight away.
	
### cb.runOrTimeout (onFire, onTimeout, duration)
1. `onFire {function}` ---Function to call if callback is or has fired.
2. `onTimeout {function}` ---Function to call if timeout occurs first.
3. `duration {number}` ---Amount of milliseconds before timeout occurs.

Run two seperate callbacks depending on whether the specified timeout occurs or the callback is triggered.

### cb.chain (id)
1. `id {number}`
2. Return: `{function}`

Returns a function that will not trigger the callbacks until all functions created by this is executed. The callback will be fired when every function created by `chain()` is executed. It essentially increases a pending counter, while the function it returns decreases it and if `0`, `fire()`.

### cb.fire ([args ...])

Fire all the registered callbacks. Any arguments passed to this will be passed into the registered callbacks.

### cb.fired ()
1.	Return: `{boolean}`

Check if the callback chain has been fired.

### cb.reset ()

Allow the callback chain to be fired again.

### cb.clear ()

Clears all of the registered callbacks.

### cb.forward (args)
1. `args {array}`

Apply the `args` array as arguments to `cb.run()`.