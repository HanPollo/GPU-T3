# Tarea3-GPU
 Tarea 3 de computacion en GPU
# Compilation
clone the repo to the desired folder:
```
git clone --recursive https://github.com/HanPollo/GPU-T3.git
```
Once downloaded open t3GPU folder with Visual Studio or with a terminal that suports cmake commands

1- Go to t3GPU folder in terminal (that supports mkdir and cmake commands, preferably Visual Studio's Developer PowerShell as it is done in demo)

2- Write the following code:
```
mkdir build
cd build
cmake ..
cmake --build .  //Or alternatevily Open t3GPU/build/t3GPU.sln with Visual Studio and build all solutions
```
Back in terminal make sure you are on t3GPU/build and run the following code to see demo:
```
cd source/Debug
./t3.exe
```
