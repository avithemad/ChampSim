# Readme for reproducing problem 1 results

The storage budget for each branch predictor were calculated as to use maximum and not exceed 128KB. The parameters that were changed in each source file corresponding to each variant mentioned in the report are given for each branch predictor scheme in the following sections.

## GShare

Following parameters in the `branch/gshare/gshare.cc` file were changed

| Variant | GLOBAL_HISTORY_LENGTH | COUNTER_BITS | GS_HISTORY_TABLE_SIZE |
| ------- | --------------------- | ------------ | --------------------- |
| 1       | 19                    | 2            | 524288                |
| 2       | 18                    | 3            | 262144                |
| 3       | 18                    | 4            | 262144                |

## Perceptron

Following parameters in the `branch/perceptron/perceptron.cc` file were changed

| Variant | PERCEPTRON_HISTORY | PERCEPTRON_BITS | NUM_PERCEPTRONS |
| ------- | ------------------ | --------------- | --------------- |
| 1       | 130                | 8               | 1000            |
| 2       | 260                | 8               | 500             |
| 3       | 130                | 16              | 500             |
| 4       | 260                | 16              | 250             |

## Tage

Following parameters in the `branch/tage/tage.cc` file were changed

| Variant | TAGE_BIMODAL_TABLE_SIZE | TAGE_MAX_INDEX_BITS | TAGE_NUM_COMPONENTS | TAGE_BASE_COUNTER_BITS | TAGE_COUNTER_BITS | TAGE_MIN_HISTORY_LENGTH | TAGE_INDEX_BITS[TAGE_NUM_COMPONENTS] | TAGE_TAG_BITS[TAGE_NUM_COMPONENTS] |
| ------- | ----------------------- | ------------------- | ------------------- | ---------------------- | ----------------- | ----------------------- | ------------------------------------ | ---------------------------------- |
| 1       | 262144                  | 13                  | 4                   | 2                      | 3                 | 4                       | {13, 13, 13, 13}                     | {10,10,10,10}                      |
| 1       | 262144                  | 13                  | 4                   | 2                      | 3                 | 8                       | {13, 13, 13, 13}                     | {10,10,10,10}                      |
| 2       | 131072                  | 14                  | 4                   | 2                      | 3                 | 4                       | {14, 14, 14, 14}                     | {6,6,6,6}                          |
| 2       | 131072                  | 14                  | 4                   | 2                      | 3                 | 8                       | {14, 14, 14, 14}                     | {6,6,6,6}                          |
| 3       | 262144                  | 12                  | 4                   | 3                      | 3                 | 4                       | {12, 12, 12, 12}                     | {8,8,8,8}                          |
| 3       | 262144                  | 12                  | 4                   | 3                      | 3                 | 8                       | {12, 12, 12, 12}                     | {8,8,8,8}                          |

## Hybrid - Tage and Perceptron

Following parameters in the `branch/perceptron-tage/perceptron-tage.cc` file were changed

| Variant | TAGE_BIMODAL_TABLE_SIZE | TAGE_MAX_INDEX_BITS | TAGE_NUM_COMPONENTS | TAGE_BASE_COUNTER_BITS | TAGE_COUNTER_BITS | TAGE_MIN_HISTORY_LENGTH | TAGE_INDEX_BITS[TAGE_NUM_COMPONENTS] | TAGE_TAG_BITS[TAGE_NUM_COMPONENTS] | PERCEPTRON_HISTORY | PERCEPTRON_BITS | NUM_PERCEPTRONS |
| ------- | ----------------------- | ------------------- | ------------------- | ---------------------- | ----------------- | ----------------------- | ------------------------------------ | ---------------------------------- | ------------------ | --------------- | --------------- |
| 1       | 262144                  | 12                  | 4                   | 2                      | 3                 | 4                       | {12, 12, 12, 12}                     | {7,7,7,7}                          | 250                | 8               | 150             |
| 2       | 131072                  | 11                  | 4                   | 3                      | 3                 | 4                       | {11, 11, 11, 11}                     | {9,9,9,9}                          | 250                | 8               | 250             |
| 3       | 65536                   | 11                  | 4                   | 2                      | 3                 | 4                       | {11, 11, 11, 11}                     | {7,7,7,7}                          | 250                | 11              | 250             |

## Running the simulation

In order to reproduce the results obtained in the report,

-   update the source file with any of the configuration in the above sections.
-   Change the parameter in the `champsim_config.json` file
    `            "branch_predictor": "gshare",`
-   Run `make`
-   Run the following by replacing `<path to trace file>` with any of the path of the trace file in traces/ folder.
    `./bin/champsim --warmup_instructions 200000000 --simulation_instructions 500000000 <path to trace file>`
