
build/bill: | build/ 
	touch $@

build/bob: build/bill | build/
	touch $@

build/rob: | build/bob build/
	touch $@

build/:
	mkdir -p $@

clean:
	rm -rf build