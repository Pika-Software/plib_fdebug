# FDebug
Debug library extension that adds some useful functions in it.

## Functions

### `debug.fempty()`
- Return: empty `function`
- Example:
    ```lua
    local func = debug.fempty()
    print( isfunction( func ), func, func() )
    ```
    - Output:
        - `true`
        - `function: xxxxxxxx`
        - `nil`

### debug.getfname( `function` searchable, `number` level )
- Return: function name `string`.
- Example:
    ```lua
    print( debug.getfname( print ) )
    ```
    - Output:
        - `print`

### debug.getf( `strign` name )
- Return: `function` or `nil` if function does not exist.

### debug.setf( `function` func, `boolean` override )
- Return: `function`
- Example:
    ```lua
    local func = debug.setf( print, false )

    local counter = 0
    function print( ... )
        counter = counter + 1
        func( counter .. '.', ... )
    end

    print( debug.getf( print ) == func )
    print( debug.getf( print ) == print )
    ```
    - Output:
        - `1. true`
        - `2. false`
