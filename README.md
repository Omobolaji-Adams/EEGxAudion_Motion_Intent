## Hybrid Human-Machine Interface for Enhanced Wheelchair Control
This project implements a hybrid human-machine interface for enhanced wheelchair control, combining EEG-based motion intent prediction with speech recognition. It utilizes a Muse 2 headband for EEG data and a microphone for voice commands. The system is currently prototyped using a Picar robot on a Raspberry Pi.

## Project Overview
The goal of this project is to create an intuitive and efficient control system for wheelchairs, enhancing mobility for individuals with limited physical capabilities. By combining EEG signals and voice commands, the system aims to provide a more natural and accessible interface for wheelchair users.
Key features:

EEG-based motion intent prediction using Muse 2 headband
Speech recognition for voice command input
Integration of EEG and voice data for enhanced control
Prototype implementation on a Picar robot

## Hardware Requirements

- Raspberry Pi (tested on [specify your Raspberry Pi model])
- Picar robot
- USB microphone
- Muse 2 headband
- Bluetooth adapter (if not built into your Raspberry Pi)

## Software Requirements

- Raspberry Pi OS (tested on [specify your OS version])
- Python 3.x
- pip (Python package installer)

## Installation

1. Clone this repository to your Raspberry Pi:
   ```
   git clone https://github.com/Omobolaji-Adams/Hybrid-Human-Interface.git
   cd Hybrid-Human-Interface
   ```

2. Install Picar modules:
   Follow the instructions provided on the [Picar website](https://docs.sunfounder.com/projects/picar-x/en/latest/python/python_start/install_all_modules.html) to install the necessary modules.

3. Install project dependencies:
   ```
   cd Project
   pip install -r requirements.txt
   ```

4. Install MuseLSL:
   ```
   pip install muselsl
   ```

5. Ensure you have the required TFLite models in your project directory:
   - `simple_cn_classification_model.tflite` (EEG model)
   - `model_update.tflite` (Voice model)

## Setting up the Muse 2 Headband

1. Install `bluetoothctl` if not already available:
   ```
   sudo apt-get update
   sudo apt-get install bluetooth pi-bluetooth bluez
   ```

2. Connect the Muse 2 headband:
   ```
   bluetoothctl
   [bluetooth]# scan on
   [bluetooth]# pair [Muse MAC Address]
   [bluetooth]# trust [Muse MAC Address]
   [bluetooth]# connect [Muse MAC Address]
   [bluetooth]# quit
   ```

## Running the Project

1. Open two terminal windows.

2. In the first terminal, start the MuseLSL stream:
   ```
   muselsl stream
   ```

3. In the second terminal, navigate to your project directory and run the main script:
   ```
   cd Hybrid-Human-Interface/Project
   python3 combined_control.py --use_muse --eeg_model simple_cn_classification_model.tflite --voice_model model_update.tflite
   ```

## Usage

- Speak voice commands into the USB microphone to control the Picar.
- The Muse 2 headband will provide additional input for more precise control.
- Available commands: [start, stop, left, right, faster, slower]

## Troubleshooting

- If you encounter permission issues, you may need to run the script with `sudo`.
- Ensure all cables are properly connected and the Muse 2 headband is charged.
- If the Muse 2 headband doesn't connect, try restarting the Bluetooth service:
  ```
  sudo service bluetooth restart
  ```

## Contributing


## License

[Specify your project's license]
