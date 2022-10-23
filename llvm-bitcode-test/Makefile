.PHONY = run jit build-llvm disassemble-llvm disassemble-native assemble-native run-binary clean

hello: hello.c
	clang -O3 -emit-llvm hello.c -c -o hello.bc

run: hello
	./hello

jit: hello
	lli hello.bc

disassemble-llvm: hello
	llvm-dis -o hello.ll < hello.bc

disassemble-native: hello
	llc hello.bc -o hello.s

assemble-native: hello
	gcc hello.s -o hello.native

run-binary: assemble-native
	./hello.native

clean:
	-rm hello
	-rm hello.bc
	-rm hello.ll
	-rm hello.native
	-rm hello.s