
# A target takes to form of a string with a list of instructions

target1:
	echo hello world

# By default make show the commands being run.  To silence this, add a @ to the beginning of the line
target2:
	@echo hello world


# Make targets can be used to hit other targets.  The listed
target3: target2
	@echo goodbye world


# To hide targets from being tab autocompleted, prefix a .
.dependecy1:
	@echo dep 1

.dependecy2:
	@echo dep 2

.dependecy3:
	@echo dep 3

# target can call multiple other targets
target4: .dependecy1 .dependecy2 .dependecy3 