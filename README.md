### Reproducer for bazel test coverage problem


````
  $ bazel coverage --test_output=all src/test/java/com/example:test
````


Then check coverage.dat file:

```
================================================================================
Target //src/test/java/com/example:test up-to-date:
  bazel-bin/src/test/java/com/example/test.jar
  bazel-bin/src/test/java/com/example/test
INFO: Elapsed time: 12.977s, Critical Path: 1.65s
INFO: 21 processes: 10 remote cache hit, 11 internal.
INFO: Build completed successfully, 21 total actions
//src/test/java/com/example:test                                (cached) PASSED in 0.0s
  /home/davido/.cache/bazel/_bazel_davido/9b14fe665f0e24388271b9c75d2c17dd/execroot/__main__/bazel-out/k8-fastbuild/testlogs/src/test/java/com/example/test/coverage.dat

Executed 0 out of 1 test: 1 test passes.
INFO: Build completed successfully, 21 total actions
```

And the coverage.dat is sane:

```
$ head /home/davido/.cache/bazel/_bazel_davido/9b14fe665f0e24388271b9c75d2c17dd/execroot/__main__/bazel-out/k8-fastbuild/testlogs/src/test/java/com/example/test/coverage.dat
SF:src/main/java/com/example/Collatz.java
FN:3,com/example/Collatz::<init> ()V
FN:6,com/example/Collatz::getCollatzFinal (I)I
FNDA:0,com/example/Collatz::<init> ()V
FNDA:1,com/example/Collatz::getCollatzFinal (I)I
```

