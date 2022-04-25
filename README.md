# SynthCT Artifacts

This repository contains all SynthCT artifacts / synthesized translations during our runs
for NDSS'22. If you're looking for the code for SynthCT framework, it can be found [here](https://github.com/FPSG-UIUC/synthCT).

See individual directories for README / settings to reproduce the results.


## Results Format

The results are in a machine-readable yaml format, named `synth-instance-xxxx.yaml` in
their corresponding directories. You can load them back into python object, i.e.,
`SynthCT/synthesis/task\_result:SynthesisTaskResult`, using `yaml.load`. Make sure that
you import the `SynthesisTaskResult` class first! Each entry is a separate synthesis task
that is run. Here are some important fields from the `SynthesisTaskResult` class.

* `key` / `result.name` : Full synthesis task name. This identifier is unique.

* `result.spec` : Name of the instruction to synthesize

* `result.state` : 
     - `timeout` : Synthesis Task timedout
     - `success` : Succesfully synthesized a translation
     - `unsat` : No synthesis solution was possible (with the set of components)

* `result.data`: Contains the string version of the translation, only if the state was
  success.

* `result.debug` : Contains debug message if state was not success

* `result.is_flag_result` : Is this result for synthesizing RFLAGS?

### Debug Fields

Some fields are made available for debug / stats purposes and do not affect synthesis
results.

* `result.components` : Selected set of components for synthesis
* `result.max_timeout` : Maximum timeout set for run
* `result.time` : Duration of synthesis run

## How Do I Use These Translations?

The current set of translations are provided as is and need some work to use. Here I will outline
some of the steps needed to make these translations work. If you're interested in using
these translations, please get in touch and I'd be more than happy to work with you to
help!

1. Parse / load all `yaml` file results.
2. Filter out only runs that return `success`
3. 


## Cite

If you find our work helpful, the framework or the artifacts, please cite our NDSS'22
paper:

```
@inproceedings{synthct,
  author    = {Sushant Dinesh and
               Grant Garrett-Grossman and
               Christopher W. Fletcher
  },
  title     = {SynthCT: Towards Portable Constant-Time Code},
  booktitle = {{NDSS}},
  publisher = {The Internet Society},
  year      = {2022}
}
```

## License

MIT License

Copyright (c) 2022 Sushant Dinesh <sushant.dinesh94@gmail.com> and FPSG-UIUC group

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
