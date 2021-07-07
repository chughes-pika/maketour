# So far, while Make has provided us a safe an efficient way to build our application,
#	the system gets verbose very quickly with nested files.  The major power in Make
#	comes from the "automatic variables"

# One of the most useful variable is the target variable
build/:
	mkdir $@
# Here, the $@ takes the target (or targets) in and provides them to the command

build/file0: | build/
	@echo Making file: $@
	@echo file0 > $@


# In places where there are a lot of files that we need to track, we can start to capture them into variables
WATCH_FILES = $(shell find src -type f) # We need to tell Make to execute this in a shell (uses default system shell)
build/bigFile.bin: ${WATCH_FILES} | build/
	@echo 'Compiling' the $(@F) in the $(@D) directory
	cat $? > $@
# Here we see a few variables used
#	$(@F) grabs only the file name of the target
#	$(@D) grabs only the directory of the target
#	$? provides a space delimited list of all the prerequists

# This is somewhat helpful, but instead fo taking dozens of files and compiling them into a single target, what if we need 1-to-1
#	mapping between inputs and outputs (A very common pattern in C/C++ development turning .c files into .o files) 


# To achieve this, we can use Make's built in pattern matching
build/%.bin: src/%.src | build/
	@echo "'Compiling' file with stem $*"
	@cp $? $@
	@echo "compiled" >> $@

# For 'file1', the above target translates into
#	build/file1.bin: src/file1.src | build/
#		@echo "'Compiling' file with stem file1"
#		@cp $? $@
#		@echo "compiled" >> $@
#
# 	for each file in the src/ directory.

# $* lists the value of the pattern matched section (what the % masks)

# So now there are targets build/file1.bin build/file2.bin etc... but boy it would be painful to compile all of those.
# 	to expidite the process, lets go ahead and make a phony for this build
build_all: $(shell find src -type f | sed 's/src/build/' | sed 's/.src/.bin/')
# Now that's much better!

clean:
	rm -rf build/
