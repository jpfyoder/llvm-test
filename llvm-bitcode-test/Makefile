.PHONY = run jit build-llvm disassemble-llvm disassemble-native assemble-native run-binary

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