KONANC=${KONAN_HOME}/bin/kotlinc-native
JAVA_OPTS_VALUE=""
ifdef DEBUG
JAVA_OPTS_VALUE="-agentlib:jdwp=transport=dt_socket,server=y,suspend=y,address=5005"
endif

terminator.kexe: hello.kt
	JAVA_OPTS=$(JAVA_OPTS_VALUE) ${KONANC} \
	-verbose \
	-g \
	-Xverbose-phases=ObjectFiles \
	-Xsave-llvm-ir-after=LinkBitcodeDependencies -Xsave-llvm-ir-directory=. \
    $^ -o $@

global-symbols.txt: terminator
	nm -g -U $^ > $@

clean:
	rm -rf terminator.kexe terminator.kexe.dSYM *.ll
