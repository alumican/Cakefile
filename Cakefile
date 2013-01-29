define = () ->

	setTask('libname1', [
		'source'
		'coffeefile'
		'without/extension'
	], './path/to/src/base/directory', './path/to/output/directory')

	setTask('libname2', [
		'other'
		'task/here'
	])





##################################################
#This script depends on following packages.
#npm install muffin
#npm install util
#npm install q
muffin = require 'muffin'
util = require 'util'
require 'q'

LOG = true

option '-m', '--minify', 'Minify JavaScript (original.min.js)'
option '-w', '--watch', 'Watch files for changes, rerunning the specified command when any file is updated.'
option '-b', '--bare', 'Compile the JavaScript without the top-level function safety wrapper.'

setTask = (id, srcfiles, srcdir = '.', outputdir = '.') ->
	task id, "build #{outputdir}/#{id}.js", (options) -> compile id, srcfiles, srcdir, outputdir, options

compile = (id, srcfiles, srcdir, outputdir, options) ->
	log 'gathering source files...'
	files = srcfiles.concat()
	for filename, index in srcfiles
		files[index] = "#{srcdir}/#{filename}"
		log "#{(' ' + (index + 1)).substr -2, 2}) #{srcdir}/#{filename}"
	log 'compiling...'
	option = ''
	option += ' -l'
	option += ' -w' if options.watch?
	option += ' -b' if options.bare?
	log "compile options#{option}"
	option += " -cj #{outputdir}/#{id}.js #{files.join(' ')}"
	q = muffin.exec "coffee #{option}"
	next q[1], 'compile', "#{outputdir}/#{id}.js", () -> minify id, outputdir if options.minify

minify = (id, outputdir) ->
	log 'minifying...'
	q = muffin.minifyScript "#{outputdir}/#{id}.js"
	next q, 'minify', "#{outputdir}/#{id}.min.js"

next = (q, name, file, f = null) ->
	q.then(
		() -> 
			log "#{name} succeeded -> #{file}"
			f.call(null) if f?
		() ->
			log "#{name} failed"
	)

log = (m) -> util.log m if LOG

define()