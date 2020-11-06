/**
 * @author Shawn Storm (storm.shwn@gmail.com)
 *
 * @brief This script runs everything needed to 
 * get the Alazar drivers, Anaconda, Qcodes and 
 * the IBM software up and running.
 * 
 * @section DESCRIPTION
 * Read through this README file to make sure
 * everything gets installed correctly. After 
 * running the script and items in this file, the user 
 * should have everything to run Qcodes and the IBM 
 * software. Be sure to follow all commands and run
 * the commands in the "After Installation" section.
 * Enjoy!
**/

To run the script run the following commands:

cd $HOME/drivers
chmod +x alazar
./alazar
-----------------------------------------------
--------------Alazar Drivers-------------------

If you want to check if the Alazar drivers were successfully installed,
run the AlazarFrontPanel application by clicking the Super key and beginning
to type in "AlazarFrontPanel" an app should pop up. After opening the program,
you should see an oscilloscope GUI. This means that the drivers were successfully
installed. Otherwise, an error would show stating "Error: No systems were found."
There shouldn't be an error showing. If so, something is wrong with the kernels. 
Though this was already solved. 
-----------------------------------------------
--------------Anaconda-------------------------

1. The recommended install location should be %HOME (i.e. /home/badXXX/). 
Use this location.

2. At the end of the installation, the installer prompts “Do you wish the 
installer to initialize Anaconda3 by running conda init?” Type in “yes”.

3. Make sure you are in the correct environment. Qcodes and the IBM Software
have their own dedicated environment. 

4. The Anaconda .sh is there only to save time and could/should be updated
to the newest version (isn't mandatory). If you want to update Anaconda 
to the newest version, run in the terminal: conda update conda

-----------------------------------------------
--------------IBM Software---------------------

1. This is a caveat: depending on what you use/need from the IBM Software, you 
may need to install additional packages onto the computer. Make sure you are
in the qc_code3 environment in case these are python packages. Run
"conda activate qc_code3" to make sure you are in the environment (it usually shows 
on the left-hand side if you are there). If you get any errors, read the 
last "XXXXError" line on the terminal. That file is usally the file that needs to 
be installed (Google is your friend!).

-----------------------------------------------
-------------After Installation----------------

After the script has successfully finished:

1. Go into:

$HOME/Qcodes/qcodes/instrument_drivers/AlazarTech/

and replace ATS.py and ATS9440.py with the two files in the qcodes_files/ folder.
This however, will be obsolete around end of November/beginning of December
as the Linux versions of ATS.py and ATS9440.py will be integrated into Qcodes.

Now the ATS package from Qcodes will run on Linux

2. After the script is finished running, run:
sudo nano .bashrc
and then scroll to the bottom and paste the following command:
source $HOME/sw-backend-qc-code/ibmqc_package/etc/bashrc
Exit and save (Ctrl+X then press y and ENTER).
This adds the qc_code3 env to the bash. 

3. You need to make sure that conda is working in the terminal (test by running
conda --version in the terminal). It might also run now but then when starting 
a new terminal it could not work anymore. If conda doesn't work run:
sudo nano .bashrc
and scroll to the bottom and paste the following into the file:
export PATH=~/anaconda3/bin:$PATH
exit and run:
source ./bashrc
Try:
conda --version
in the terminal. It should work now. 

