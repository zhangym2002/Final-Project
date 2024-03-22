## Target

mean of 50% and 95% distribution of 2D errors  
test: Phone model appears in train set at least once, not in train, public/private test random split

## Doc & Data

Ground truth: Interpolated ground truth values at GNSS time

- verified
- foundation of SDC

device_gnss.csv: Raw and derived GNSS values

- Raw values
- Derived values: calculated from raw values

## Filters
-  BiasUncertaintyNanos is too large
-  Full bias nanoseconds is zero or invalid
-  Arrival time is negative or unrealistically large
-  TimeNanos is empty
-  Either ChipsetElapsedRealtimeNanos or ElapsedRealtimeNanos is not available (risky)
-  Tectonic movement in Western US: 1-5cm/yr

## Leading solutions

- Factor Graph Optimization
- Post-processed kinematic
- FGO + TensorFlow

## Abbr.

ADR: Accumulated Delta Range  
IMU: Inertial Measurement unit  
GNSS: Global Navigation Satellite System  
GT: Ground Truth  
AGC: Automatic Gain Controller Value  
NMEA: National Marine Electronic Association
PCO and PCV: Phase Center Offset and Variations

## Questions
- Not all files have available ChipsetElapsedRealtimeNanos and ElapsedRealtimeNanos, so have to take risks to use others.
- SDC collection contains more than 200,000 epochs with verified GT and the usage of the datasets is allowed. Difficult to train the model on my PC only, and need more computational resource.