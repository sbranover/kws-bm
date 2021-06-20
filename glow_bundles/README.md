# GLOW Bundles
This is the model used to generate the glow bundles for the benchmark.

The model is the Keyword Spotting model from the [MLPerf Benchmark](https://github.com/mlcommons/tiny/blob/master/v0.5/training/keyword_spotting/trained_models/kws_ref_model.tflite)

To generate the bundles, you can build the GLOW Compiler from [source](https://github.com/pytorch/glow) or download the windows executable [from NXP](https://www.nxp.com/design/software/development-software/eiq-ml-development-environment/eiq-for-glow-neural-network-compiler:eIQ-Glow?&tab=Design_Tools_Tab).

To build for a Cortex-M7 use:
```
model-compiler -model=.\kws_ref_model.tflite -backend=CPU ^
-emit-bundle=bundle_m7_hfp_cmsis -target=arm -mcpu=cortex-m7 ^
-float-abi=hard -use-cmsis
```

To build for a Cortex-M33 use:
```
model-compiler -model=.\kws_ref_model.tflite -backend=CPU ^
-emit-bundle=bundle_m33_hfp_cmsis -target=arm -mcpu=cortex-m33 ^
-float-abi=hard -use-cmsis
```