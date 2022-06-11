# Optimized OpenSimplexNoise

This repo contains optimized versions of Legacy OpenSimplexNoise from https://github.com/KdotJPG/OpenSimplex2, and OpenSimplex2SCachedColumnNoise from https://github.com/KdotJPG/Noise-Extras (ColumnOpenSimplexNoise).

From Java Micro Harness and real-world tests, these optimizations provide a 5-15% performance uplift in ideal conditions, compared to the regular versions. This speed comes from restructuring the code, utilizing FMA instructions, and more optimized math. However, this depends on your access pattern of the noises. In some cases, the performance benefit is lower or possibly even none at all. The exact CPU and Java version you're using also changes the performance of these classes, as this depends on some finnicky code to trick the JVM to inline and optimize in a certain way. If your system is not getting any benefit from this code please open an issue, and I'll see if it can be fixed.

Extra care has been taken to make sure that the behaviors of these noises are similar to the unoptimized versions. However, using FMA instructions causes precision differences compared to non FMA code. Therefore, the new versions are only similar up to 5 decimal places. To ensure that the output is bit-identical, FMA can be disabled in the code, by searching for the "fma" function.


### Future Work
- The regular open simplex noise code could use another pass, to clean up todos and fix up the rest of the branchy code.
- Provide versions that use the Vector API.
- Optimize the other methods and other noises.


### DISCLAIMER
This code is provided as-is, under a CC0 license.