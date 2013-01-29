# Cakefile
This script provides the simple way to join multiple CoffeeScript files, compile, and minify.  
This cakefile depends on npm packages [muffin](https://github.com/hornairs/muffin), [q](https://github.com/kriskowal/q), and [util](https://npmjs.org/package/util).

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
+ `'-m' or '--minify'` :  
    Minify JavaScript.

+ `'-w' or '--watch'` :  
    Watch files for changes, rerunning the specified command when any file is updated.

+ `'-b' or '--bare'` :  
    Compile the JavaScript without the top-level function safety wrapper.