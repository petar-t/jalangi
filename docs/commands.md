## esnstrument.js

Command-line utility to perform instrumentation

	node src/js/instrument/esnstrument.js -h
	usage: esnstrument.js [-h] [--metadata] [--maxIIDsFile MAXIIDSFILE] ...

Positional arguments:

	files                 files to instrument

Optional arguments:

	-h, --help            Show this help message and exit.
  	--metadata            Collect metadata
  	--maxIIDsFile MAXIIDSFILE
                          File containing max IIDs


## instrumentDir.js

Utility to apply Jalangi instrumentation to all files in a directory

	node src/js/commands/instrumentDir.js -h
	usage: instrumentDir.js [-h] [-s] [-x EXCLUDE] [-i]
                        [--jalangi_root JALANGI_ROOT] [--analysis ANALYSIS]
                        [-d] [--selenium] [--in_memory_trace] [--inbrowser]
                        [--smemory] [--relative] [-c] [--first_iid FIRST_IID]
                        [--extra_app_scripts EXTRA_APP_SCRIPTS] [--no_html]
                        inputDir outputDir


Positional arguments:

	inputDir              directory containing files to instrument
  	outputDir             directory in which to create instrumented copy

Optional arguments:

	-h, --help            Show this help message and exit.
  	-s, --serialize       dump serialized ASTs along with code
  	-x EXCLUDE, --exclude EXCLUDE
                        do not instrument any scripts whose filename contains 
                        this substring
  	-i, --instrumentInline
                        instrument inline scripts
  	--jalangi_root JALANGI_ROOT
                        Jalangi root directory, if not working directory
  	--analysis ANALYSIS   Analysis script for 'inbrowser'/'record' mode. 
                        Analysis must not use ConcolicValue
  	-d, --direct_in_output
                        Store instrumented app directly in output directory 
                        (by default, creates a sub-directory of output 
                        directory)
  	--selenium            Insert code so scripts can detect they are running 
                        under Selenium. Also keeps Jalangi trace in memory
  	--in_memory_trace     Insert code to tell analysis to keep Jalangi trace in 
                        memory instead of writing to WebSocket
  	--inbrowser           Insert code to tell Jalangi to run in 'inbrowser' 
                        analysis mode
  	--smemory             Add support for shadow memory
  	--relative            Use paths relative to working directory in injected 
                        <script> tags
  	-c, --copy_runtime    Copy Jalangi runtime files into instrumented app in 
                        jalangi_rt sub-directory
  	--first_iid FIRST_IID
                        initial IID to use during instrumentation
  	--extra_app_scripts EXTRA_APP_SCRIPTS
                        list of extra application scripts to be injected and 
                        instrumented, separated by path.delimiter
  	--no_html             don't inject Jalangi runtime into HTML files

## direct.js

Command-line utility to perform Jalangi's direct analysis

	node src/js/commands/direct.js -h
	usage: direct.js [-h] [--smemory] [--analysis ANALYSIS] ...


Positional arguments:
  
	script_and_args      script to record and CLI arguments for that script

Optional arguments:
  
	-h, --help           Show this help message and exit.
    --smemory            Use shadow memory
    --analysis ANALYSIS  absolute path to analysis file to run

## record.js

Command-line utility to perform Jalangi's record phase

    node src/js/commands/record.js --help

    usage: record.js [-h] [--smemory] [--tracefile TRACEFILE]
                     [--analysis ANALYSIS]
                     ...

Positional arguments:

    script_and_args       script to record and CLI arguments for that script

Optional arguments:

    -h, --help            Show this help message and exit.
    --smemory             Use shadow memory
    --tracefile TRACEFILE
                        Location to store trace file
    --analysis ANALYSIS   analysis to run during record

## replay.js

Command-line utility to perform Jalangi's replay phase

	node src/js/commands/replay.js --help
	usage: replay.js [-h] [--smemory] [--tracefile TRACEFILE]
                 	[--analysis ANALYSIS]
                 


Optional arguments:

	-h, --help            Show this help message and exit.
	--smemory             Use shadow memory
	--tracefile TRACEFILE
                        Location to store trace file
    --analysis ANALYSIS   analysis to run during replay
    
## symbolic.js

Command-line utility to perform Jalangi's pure symbolic execution

	node src/js/commands/symbolic.js -h
	usage: symbolic.js [-h] analysis ...


Positional arguments:
  
	analysis         absolute path to symbolic execution code
	script_and_args  script to run symbolically and its arguments

Optional arguments:
  
	-h, --help       Show this help message and exit.
	