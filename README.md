# Audio Amplifier — LTspice

A low-distortion Class AB audio power amplifier designed and simulated in LTspice.

The amplifier uses a MOSFET differential input stage, voltage gain stage, buffer stage, and push-pull Class AB output stage with global negative feedback. The design was evaluated under DC, transient, AC, frequency/phase, distortion, power, PSRR, input/output resistance, and real-audio test conditions.

## Features

* Class AB push-pull output stage
* MOSFET differential input stage
* Voltage gain and buffer stages
* Global negative feedback
* Current-mirror bias/reference circuitry
* 50 Ω output load
* ±10 V supply rails
* Closed-loop voltage gain of approximately 20
* Real-audio simulation using WAV input/output

## Simulation Setup

| Parameter               |           Value |
| ----------------------- | --------------: |
| Supply voltage          |   +10 V / −10 V |
| Load resistance         |            50 Ω |
| Feedback resistor, Rf   |          190 kΩ |
| Feedback resistor, Rg   |           10 kΩ |
| Target closed-loop gain |            ≈ 20 |
| Nominal input           | 50 mV amplitude |
| Test frequency          |           1 kHz |

The closed-loop gain is primarily set by the feedback network:

**Gain ≈ 1 + Rf/Rg = 20**

The amplifier was also tested at large output swing to evaluate clipping, efficiency, and output-stage behavior.

## Analyses

The project includes LTspice simulations for:

* DC operating-point and bias analysis
* Transient analysis
* AC/frequency sweep
* Phase sweep
* Fourier analysis and THD
* Output-stage power and efficiency
* Power-supply rejection ratio (PSRR)
* Differential input resistance
* Output resistance
* Large-signal output swing
* Real-audio signal processing

## Key Results

| Metric                        |    Result |
| ----------------------------- | --------: |
| Closed-loop gain              |     19.99 |
| Output swing                  | 16.97 Vpp |
| Output-stage efficiency       |    72.06% |
| Total power consumption*      | 175.48 mW |
| THD                           |    0.022% |
| THD with noisy source         |    0.463% |
| PSRR                          |  87.83 dB |
| Differential input resistance |    > 1 MΩ |
| Output resistance             |   4.90 mΩ |
| Design cost                   |       109 |

* Measured in simulation for the nominal 50 mV, 1 kHz input condition with a 50 Ω load.

The input/output resistance values are simulation/model results rather than physical measurements.

## Real Audio Test

The repository includes a separate LTspice testbench for processing a real WAV audio signal.

`LTspice/audio_test.asc`:

* reads `audio/audio.wav`
* uses a 44.1 kHz, 16-bit WAV signal
* passes the signal through the amplifier
* writes the simulated output to `audio/output.wav`

The audio testbench uses relative paths, so it should be opened from the repository with the directory structure preserved.

## Repository Structure

```text
Audio-Amplifier-LTspice/
├── LTspice/
│   ├── amplifier.asc
│   └── audio_test.asc
├── audio/
│   ├── audio.wav
│   └── output.wav
├── report/
│   └── report-fa.pdf
├── .gitignore
└── README.md
```

## Tools

* LTspice
* MOSFET and BJT device models
* WAV audio input/output

## Report

A detailed Persian-language project report is included in:

`report/report-fa.pdf`

The report contains the design process, circuit analysis, simulation results, and performance evaluation in greater detail.
