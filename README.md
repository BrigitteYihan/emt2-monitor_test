emt2-monitor
============

automatic file-monitor for emt2
The base path where all this code is stored will be referred to as $(yihan-monitor)

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% THIRD PARTY RESOURCES %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

The monitor script package uses the third party codes wini.cpp.
When using the monitor package, the wini.cpp must be installed.  The wini.cpp is a part of the apparatus3-analysis package, and is in the qini folder. When using the monitor, also go to the apparatus3-analysis repository in Github, and install the qini folder.

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% USAGE %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

The monitor script automatically and continuously detects the creation of the new .fit files when the camera takes new pictures. Then the monitor calculates the variable detune value of each shot by running the bash script detune, sends the results to sec.py. The python code sec.py reads the flags with fixed values from the master file, which is the analysis.INI here, then sends back the flags string with the detune value to the monitor and creates a corresponding report file of that shot with a "FLAGS" section that contains all the flags. The monitor then runs the analysis executable with the flags string and with another script grepQ which attains the q value needed for the analysis from the logFile. 

In this process, the a report file is created for each shot, and the analysis results of each shot are stored in a corresponding .out file. The monitor then calls the out2INI bash script which greps the information in the .out file via the different grep scripts, and stores the information under different sections in the report file using the wini.py.

Then the user can run the plotting and fitting program, plotgui, and use the information in the report file to plot and fit.

When using the monitor package, first go to the directory where the .fit files are going to be created. Run the monitor using the following command:
          $/home/yihan/monitor/monitor
When the .fit file comes in, the shot number, the flags, the analysis results, and the contents in the report file will be presented on the command window, and the corresponding .out file and report file will be created in that data folder. In order to plot and fit, use the following command:
          $/lab/software/epd-7.0-1-rh5-x86/bin/python /lab/software/apparatus3/plotgui/viewdata_win.py

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% EMT2-MONITOR HELPER OBJECTS %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

