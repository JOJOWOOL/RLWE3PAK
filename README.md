
====================================================================

This software was initially distributed by the authors from <https://github.com/dstebila/rlwekex>

We implemented our three party key exchange protocol 3PAKE on the basis of their software.

For the 3PAKE scheme, see https://eprint.iacr.org/2019/1386.


Instructions
------------
The software is plain C (C99 standard).  Compilation has been tested using gcc on Linux and clang on Mac OS X.

To compile:

	make

Note that compilation on Mac OS X with the downloaded ZIP will fail, because the library uses OpenSSL for randomness generation, and Mac OS X has an old version of OpenSSL in a peculiar location.  Either change the random number generator to the insecure one (see the instructions below) or install and use a newer version of OpenSSL (see the comments at the top of the Makefile).

To run the sample key generation program:

	./rlwe_main

To run the benchmark program:

	./rlwe_benchmark

Cryptographically secure random number generation
-------------------------------------------------
Note that the key generation and key exchange algorithms make use of a random number generator during execution.  The sampling code is configured by default to use OpenSSL's PRNG to generate a seed and expand it using AES.  Several other options are available; see `Makefile`.  C's `random()` can be used for testing purposes by defining the macro `RLWE_RANDOMNESS_USE_INSECURE_LIBC`, but this is **not secure**.  Developers can also define the `RANDOM_VARS`, `RANDOM8`, `RANDOM32`, `RANDOM64` macros with a cryptographically secure pseudorandom number generator of their own choosing.

License
-------
This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or distribute this software, either in source code form or as a compiled binary, for any purpose, commercial or non-commercial, and by any means.

See the file LICENSE for complete information.
