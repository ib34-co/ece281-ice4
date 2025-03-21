# ICE4: Stoplight

VHDL for ECE 281 [ICE4](https://usafa-ece.github.io/ece281-book/ICE/ICE4.html)

Targeted toward Digilent Basys3. Make sure to install the [board files](https://github.com/Xilinx/XilinxBoardStore/tree/2018.2/boards/Digilent/basys3).

Tested on Windows 11.

## Build the project

You can simply open `stoplight.xpr` and Vivado will do the rest!

## GitHub Actions Testbench

The workflow uses the [setup-ghdl-ci](https://github.com/ghdl/setup-ghdl-ci) GitHub action
to run a *nightly* build of [GHDL](https://ghdl.github.io/ghdl/).

The workflow uses GHDL to analyze, elaborate, and run the entity specified in the `.github/workflows/testbench.yml`.

```yaml
env:
  TESTBENCH_ENTITY: stoplight_fsm
```

If successful then GHDL will quietly exit with a `0` code.
If any of the `assert` statements fail **with** `severity failure` then GHDL will cease the simulation and exit with non-zero code; this will also cause the workflow to fail.
Assert statements of other severity levels, such as "error" will be reported, but not fail the workflow.
DOC: Used online reasources to double check code and furthermore provide a deeper analysis that revealed minor errors that where dissrupting the whole proccess
![video demo in file](MicrosoftTeams-video.mp4)
![Redlight](Media(15).jpg)
![Yellowlight](Media(16).jpg)
![Greenlight](Media(17).jpg)
![waveform](Screenshot 2025-03-15 182016.png)
