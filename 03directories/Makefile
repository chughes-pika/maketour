# This target requires the build directory, but it leads to some interesting problems. Build the 
#	next two targets
build/somefile: source build/
	@echo Making somefile
	@cat source > build/somefile
	@echo some build file >> build/somefile
	@date >> build/somefile

build/otherfile: source build/
	@echo Making otherfile
	@cat source > build/otherfile
	@echo some build file >> build/otherfile
	@date >> build/otherfile

# Now try to build somefile again

# You'll notice that it rebuilt it, but why is this?  Delete the build directory and try again in debug
#	`make clean`, `make build/somefile --debug`, `make build/otherfile --debug`, `make build/somefile --debug`

# You should notice the log message "Prerequisite 'build/' is newer than target 'build/somefile'.  This happens because modifying
#	a document in a directory updates the file's timestamp as well as the directories timestamp.  

# To fix this problem, we need to tell Make that, for a given target, a prerequisite must exist, 
# 	but not be "up to date".  To do this, we need some new syntax

# Here, everything after the pipe is referred to as an 'order-only prerequisite'.  We only care that these files exist
build/somefile1: source | build/
	@echo Making somefile1
	@cat source > build/somefile1
	@echo some build file >> build/somefile1
	@date >> build/somefile1

build/otherfile1: source | build/
	@echo Making otherfile1
	@cat source > build/otherfile1
	@echo some build file >> build/otherfile1
	@date >> build/otherfile1

# Attempting to rebuild the above files won't cause your full build to continually rebuild.


# Skip these targets
clean:
	rm -rf build/

build/:
	mkdir build
