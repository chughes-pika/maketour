# Fundamentaly, Make is used to build files.

# Targets are generally responsible for generating a file of the same name.  Targets that do not are referred to as PHONY targets.

# Run this target twice
somefile:
	@echo hello from some file > somefile
	@date >> somefile

# Make uses the timestamp on files to determine when a file was last built

# Just like with PHONY targets, Make can call a set of dependencies
otherfile: somefile
	@cat somefile > otherfile
	@echo hello from another file >> otherfile
	@date >> otherfile


# Try running 'otherfile' twice

# You should notice that you get the message that 'otherfile' is up to date

# Now delete 'somefile' and try to build again

# In this case, both files get rebuilt.  'somefile' is rebuilt because it doesn't exist
# 	'otherfile' is built because the timestamp on 'somefile' is newer than 'otherfile'
