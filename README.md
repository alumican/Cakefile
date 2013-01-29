# Cakefile
This script provides the simple way to join multiple CoffeeScript files, compile, and minify.

## Define tasks
```coffeescript
define = () ->

    #setTask(
    #    'Output JavaScript file name (without extension)', 
    #    ['Array of source CoffeeScript file names (without extension)', ...], 
    #    'Base directory of source files (if omitted, this is directory at Cakefile)', 
    #    'Directory of output file (if omitted, this is directory at Cakefile)'
    #)

    setTask('mylib1', [
        'source'
        'coffeefile'
        'without/extension'
    ], './path/to/src/base/directory', './path/to/output/directory')

    setTask('mylib2', [
        'other'
        'task/here'
    ])
```

## Just do it
```
%cake mylib1
%cake -m -w -b mylib2
```

## Compile options
option '-m', '--minify', 'Minify JavaScript (original.min.js)'
option '-w', '--watch', 'Watch files for changes, rerunning the specified command when any file is updated.'
option '-b', '--bare', 'Compile the JavaScript without the top-level function safety wrapper.'