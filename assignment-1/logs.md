This is a document to track the progress by performing various experiments on assignment.

## Problem

Goal

Evaluate 3 benchmarks, which can be found in the link https://dpc3.compas.cs.stonybrook.edu/champsim-traces/speccpu/

-   649.fotonik3d_s-8225B.champsimtrace.xz - Avinash
-   607.cactuBSSN_s-4248B.champsimtrace.xz - Naman
-   623.xalancbmk_s-325B.champsimtrace.xz - Shubham

For the following branch predition schemes

-   G Share (Available in champsim)
-   Perceptron (Available in champsim)
-   Tage (Took the code from https://github.com/KanPard005/RISCY_V_TAGE/blob/master/branch/tage.h)

#### Sept 23, Avinash

-   Forked the champsim repository to collaborate and work on the assignment.
-   Have added the tage and hybrid predictors, we need to be careful with the budget size of the branch predictors.

Given hardware cost is 128KB, give or take 2KB.

TODO: Estimate the sizing for each branch prediction scheme

So for the perceptron,

=== Simulation ===
CPU 0 runs /Users/avithemad/Downloads/649.fotonik3d_s-8225B.champsimtrace.xz
Region of Interest Statistics

Comments -> 0.004384 seems suspicious, it may be that the number of branch instructions in the trace might be less or ... TODO, find more reasons

CPU 0 cumulative IPC: 1.205 instructions: 250000002 cycles: 207418685
CPU 0 Branch Prediction Accuracy: 99.98% MPKI: 0.004384 Average ROB Occupancy at Mispredict: 352
Branch type MPKI
BRANCH_DIRECT_JUMP: 0
BRANCH_INDIRECT: 0
BRANCH_CONDITIONAL: 0.00438
BRANCH_DIRECT_CALL: 0
BRANCH_INDIRECT_CALL: 0
BRANCH_RETURN: 0

DRAM Statistics

Channel 0 RQ ROW_BUFFER_HIT: 92940
ROW_BUFFER_MISS: 2104045
AVG DBUS CONGESTED CYCLE: 3.977
WQ ROW_BUFFER_HIT: Channel 0
ROW_BUFFER_MISS: 658743
FULL: 1532661
