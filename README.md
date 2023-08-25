# PhotoElectrochemical_Simulator
Photoelectrochemical Cell Simulator
Introduction
Photoelectrochemical Solar Cells
Photoelectrochemical solar cells (PECs) offer an innovative solution to the challenges of conventional photovoltaic devices, such as high costs and limited energy storage. These cells can directly convert solar energy into hydrogen fuel, which can then be stored and used to generate electricity when needed. This simulator focuses on modeling the reactive interface between a semiconductor and electrolyte in a 1D configuration, representing a "half cell" of a photoelectrochemical cell. This simulation addresses the complex dynamics of PECs, characterized by nonlinearity and disparate time scales between semiconductor and electrolyte charge carriers.

A typical PEC consists of four primary components: a solid semiconductor electrode, a liquid electrolyte, the semiconductor-electrolyte interface, and a counter electrode (which can be made of metal or semiconductor). When sunlight hits the semiconductor, it generates electron-hole pairs. An internal electric field in the semiconductor separates these carriers, creating an electrical current. Charges accumulate at the semiconductor-electrolyte interface, where photo-generated electrons or holes initiate chemical reactions at the semiconductor electrode. Similar reactions occur at the counter electrode, leading to the production of hydrogen fuel through changes in redox species in the electrolyte.

Software Overview
This software serves as a tool to simulate the behavior of the reactive interface between a semiconductor and an electrolyte in a 1D PEC system. The simulation faces significant challenges due to the system's highly nonlinear nature and the different time scales of semiconductor and electrolyte charge carriers. Boundary layer formations, where abrupt changes in densities and electric potential occur near the interface, introduce numerical stability constraints.

Simulation results are stored in .dat files and can be visualized using the provided Python script, plotter.py, located in the /run/ directory. The simulation output offers insights into various parameters, including densities, electric potential, and current distribution.

The software also supports parallel processing using OpenMP for multithreading, enhancing performance on multi-core systems.

Dependencies
To run the software, you need the following dependencies:

CMAKE 2.8 (Required)
GSL 1.16 (Required)
EIGEN 3.0 (Required)
BOOST (Required)
OpenMP (Optional)
Python, NumPy, and matplotlib for visualization (Optional)
Installation
After installing all the required dependencies, follow these steps:

Navigate to the PECS-1D/ directory.
Create a build directory: mkdir build
Change to the build directory: cd build
Run CMake to configure the project: cmake ..
Build the solar_cell_app executable: make solar_cell_app
Move the executable to the /run directory: mv solar_cell_app ../run
Usage
To utilize multithreading, set the number of threads using:

arduino
Copy code
export OMP_NUM_THREADS=num_threads
Replace num_threads with the number of available CPU cores.

Configure simulation parameters by modifying the ddp-input.ini file.

Run the simulation from the /run/ directory:

bash
Copy code
./solar_cell_app
To change doping/concentration profiles, edit the files in the ConcentrationProfile directory. Remember to recompile after any changes:

bash
Copy code
make solar_cell_app
mv solar_cell_app ../run
Simulation data is stored in files labeled StateXXXX.dat and contains information about electron and hole densities, electric fields, potentials, currents, and time.

Use the Python script plotter.py in the /run/ directory to visualize the simulation results:

Copy code
python plotter.py
To remove simulation-generated files, including .dat, .png, and .mp4 files, run:

bash
Copy code
./clean.sh
If you want to run simulations with different bias values, edit and use Runner_IV.py.

Testing
To test the software, run the following commands from the build/ directory:

Build the test suite: make test_System
Run the tests: ./test_System
You will receive a report indicating whether the code passed all the tests.
