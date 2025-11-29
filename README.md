# Neuromorphic-Circuit-Simulation

**Overview**
- **Project:**: A collection of LTSpice circuit simulations and reports that implement and explore neuromorphic (biologically inspired) electronic circuits.
- **Goal:**: Model neuron-like behavior (e.g., Leaky Integrate-and-Fire), synaptic excitation/inhibition, and small neuromorphic networks using analog circuit building blocks (op-amps, transistors, capacitors, resistors).

**Summary**
- **Approach:**: The project uses LTSpice `.asc` schematic/netlist files to build and test circuits that reproduce neural dynamics. Simulations explore pulse responses, integration and firing behavior, excitatory/inhibitory post-synaptic conduction channels, and incremental network buildup.
- **Reports:**: See `NeuromorphicCircuitPhase1.pdf` and `NeuromorphicCircuitPhase2.pdf` in this folder for the full written reports, experimental results, schematics, and discussion. (I attempted to read the PDF files programmatically but they are binary; open them locally to view full content.)

**Key Files**
- `LIF.asc`: Leaky Integrate-and-Fire neuron circuit (current injection, capacitor/resistor for membrane integration, `.tran` setups shown inside the file).
- `NeuroSim.asc`: Main neuron/circuit simulation used to study pulse responses and synaptic interactions.
- `NeuroSim-modified.asc`: Variant of `NeuroSim` with parameter or topology changes for comparative experiments.
- `NueroBuildUp.asc`: Stepwise network construction demonstrating how simple elements combine into larger neuromorphic modules.
- `ECNANuero.asc`: Extended circuit combining MOSFET/op-amp blocks and pulse sources for excitatory/inhibitory behavior and multi-block testing.
- `NeuromorphicCircuitPhase1.pdf`, `NeuromorphicCircuitPhase2.pdf`: Phase reports containing methodology, results, analysis, and conclusions.

**How to run the simulations**
- **Open:**: Launch LTSpice and open any `.asc` file in this folder (e.g., `NeuroSim.asc`).
- **Simulate:**: Use the GUI `Simulate > Run` or press the Run button. The schematics already include `.tran` lines (for example, `.tran 0 5 3` or `.tran 0 300ms ...`)—these specify transient analysis durations.
- **Probe:**: Click on nodes/wires in the schematic to view voltages or right-click components to display currents. Use the waveform viewer to measure spike timing, membrane potential, and synaptic currents.
- **Dependencies:**: Some schematics include `.include` directives for op-amp subcircuits (e.g., `OP27`, `AD820`)—ensure the referenced `.lib` files are available in your LTSpice library or adjust to generic `opamp` models.

**Design notes & observations (high level)**
- **LIF model:**: Implemented with a capacitor (membrane), a leak resistor, and a current pulse source that charges the capacitor until a threshold event (observable as a rapid change in output). Different pulse widths and amplitudes show integrative behavior and firing thresholds.
- **Synaptic channels:**: Circuits emulate excitatory and inhibitory post-synaptic currents using diode/resistor/capacitor networks and active elements to produce directional or time-dependent responses.
- **Network scaling:**: `NueroBuildUp.asc` and `NeuroSim-modified.asc` show incremental network construction—useful for observing emergent timing and interaction effects from simple building blocks.

**Next steps & suggestions**
- **Open the PDF reports locally**: For full methodology, plots, parameter tables and conclusions, open `NeuromorphicCircuitPhase1.pdf` and `NeuromorphicCircuitPhase2.pdf` with a PDF reader.
- **Run parameter sweeps**: Use LTSpice `.step` directives to sweep resistances, capacitances, or pulse amplitudes to map firing thresholds and timing.
- **Export data**: Use the waveform viewer `File > Export` to produce CSV data for offline analysis or plotting.


---