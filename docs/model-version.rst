Model Version
=============

This lists the changes to CRAM by release number.

Version 4 Releases
^^^^^^^^^^^^^^^^^^
Model version 4 releases include updated compatibility with Excel 2013 and major enhancements to the user interface.

CRAM 4.043
~~~~~~~~~~
**Release Date: February 3, 2020**

*New Feature*

1. New Exchange object added to the model. This can be found in the CRAM model ribbon "Add Exchange".

.. image:: /images/ModelVersion/model-version-add-exchange-circled.png
   :align: center
   :scale: 60%

CRAM 4.042
~~~~~~~~~~
**Release Date: September 13, 2019**

*General Update*

1. New status update when user-defined (premade) scenarios are loaded. This pop-up dialog box provides a description of the scenario that has been loaded into the model.

CRAM 4.041
~~~~~~~~~~
**Release Date: December 12, 2018**

*General Update*

1. Added code to save the ribbon handle.

CRAM 4.040
~~~~~~~~~~
**Release Date: November 16, 2018**

*New Feature*

1. Users can now save default label colors in the network schematic. 
Modified ColorObject, ColorObject2, DrawNode, and DrawMBNode to use the saved settings on the GlobalDataSheet.

CRAM 4.039
~~~~~~~~~~
**Release Date: November 9, 2018**

*General Update*

1. Changed the width of the premade scenarios to improve readability.

CRAM 4.038
~~~~~~~~~~
**Release Date: October 26, 2018**

*General Update*

1. Changed main solver loops to not throw an error if the first instream flow (ISF) convergence test doesn't converge.
Now it continues to solve the return flows (if any), and then produces an error if the second ISF convergence test doesn't converge.

CRAM 4.037
~~~~~~~~~~
**Release Date: May 21, 2018**

*Bux Fixing*

1. Added code to fix adding worksheet to Worksheet Dictionary list having to many spaces between new worksheets.
2. Added code to disable error message when the Excel Ribbon disables during workbook close.

CRAM 4.036
~~~~~~~~~~
**Release Date: April 3, 2018**

*User Interface*

1. Added a Ribbon to the application. CRAM now features a "CRAM" tab in the Excel Ribbon. This provides for a more seamless user interface.

.. image:: /images/ModelVersion/model-version-cram-menu.png
   :align: center
   :scale: 75%

CRAM 4.035
~~~~~~~~~~
**Release Date: April 3, 2018**

*User Interface*

1. Added a new navigation menu and new navigation buttons (network schematic, basin map, worksheet dictionary) to the Add-ins tab, and updated to the main XLCRAM engine.

.. image:: /images/ModelVersion/model-version-navigation-menu.png
   :align: center
   :scale: 60%

.. image:: /images/ModelVersion/model-version-new-buttons-circled.png
   :align: center
   :scale: 60%


CRAM 4.034
~~~~~~~~~~
**Release Date: February 16, 2018**

*Bug Fixes*

1. There was a problem reading Reservoir Timeseries Sheets in batch simulation mode. Versions before this would throw an error if you did a batch simulation with reservoir timeseries data sheets.

CRAM 4.033
~~~~~~~~~~
**Release Date: February 5, 2018**

*Bug Fixes*

1. Model shutdown process was producing an error that produced a popup box asking for a password. Fixed.
2. Editing the network before a run drops the object from the network data worksheets. Fixed.

CRAM 4.032
~~~~~~~~~~
**Release Date: December 12, 2017**

*General Update*

1. Added subroutine CheckNumberofStyles and DropUnusedStyles() and RemoveUnusedStyles() to the main engine to remove the bad formats that mess up model workbooks. 
These help to reduce the number of styles in a model workbook.

CRAM 4.031
~~~~~~~~~~
**Release Date: December 6, 2017**

*New Feature*

1. Added code and worksheets for PremadeScenario settings to main XLCRAM model engine.

*Bug Fixes*

1. Added module modFixUnusedStyles to the codebase. This is needed for some .xcwm model files.

CRAM 4.030
~~~~~~~~~~
**Release Date: September 6, 2017**

*Bug Fixes*

1. Changed default for ConvergenceLimit named range from FALSE (incorrect) to 0 (correct).

CRAM 4.029
~~~~~~~~~~
**Release Date: August 29, 2017**

*Bug Fixes*

1. Fixed bug in Reading Reservoir timeseries data (where evaporation data varies year to year).

CRAM 4.028
~~~~~~~~~~
**Release Date: August 24, 2017**

*Bug Fixes*

1. Changed code to fix when the cursor goes into hourglass mode.

CRAM 4.027
~~~~~~~~~~
**Release Date: August 22, 2017**

*General Update*

1. Revised model engine to allow an option to relax convergence limit in base model on the Start Simulation dialog box, which is also stored on the Global Data Sheet.

CRAM 4.026
~~~~~~~~~~
**Release Date: July 6, 2017**

*Bug Fixes*

1. Removed some #REF named ranges on the User Controls worksheet that were imported from the demo model.

CRAM 4.025
~~~~~~~~~~
**Release Date: June 16, 2017**

*Bug Fixes*

1. Fixed Goto Timeseries Data function to make sure the worksheet is visible before activating it. Otherwise it doesn't work for hidden worksheets. 

*General Update*

1. Added a parameter to the DebugNetwork() function to indicate the model problem is a convergence loop and it can't be debugged with the infeasible checker because it isn't infeasible.

CRAM 4.024
~~~~~~~~~~
**Release Date: May 31, 2017**

*Bug Fixes*

1. Fixed a bug that would develop because GlobalScalingFactor wasn't loaded when the ReadReservoirDataSheet was called and the Initial Contents value was throwing an error when reading the Worksheet Output Template. 
GlobalScalingFactor wasn't loaded and the Contents were then zero and the Initial Contents fell out of range.

CRAM 4.023
~~~~~~~~~~
**Release Date: April 21, 2017**

*Bug Fixes*

1. Fixed bug in creating new model workbook. modUserModeCustomCode wasn't being copied correctly causing new model command to fail.

CRAM 4.022
~~~~~~~~~~
**Release Date: April 19, 2017**

*User Interface*

1. Incorporated updated buttons and look for the User Controls worksheet into the main code engine.  

.. image:: /images/ModelVersion/model-version-level-of-detail.png
   :align: center
   :scale: 75%

*General Update*

1. Added DropUnusedStyles() to the OverheadCode module so that it can be used in new models to fix errors where workbooks contained too many styles.

CRAM 4.021
~~~~~~~~~~
**Release Date: April 5, 2017**

*General Update*

1. Added code to make sure worksheets are visible before activating them.

CRAM 4.020
~~~~~~~~~~
**Release Date: March 13, 2017**

*General Update*

1. Removed Binary Output code
2. Added Worksheet Dictionary, User Controls, and ObjectiveFunctionDefinition worksheet to the default CRAM package.

*General Update*

1. Added code to turn off StatusBar messages as an option on a Single Scenario run.

CRAM 4.019
~~~~~~~~~~
**Release Date: February 1, 2017**

*Enhanced Feature*

1. OWRB Release for Reservoir Timeseries capabilities.

CRAM 4.017
~~~~~~~~~~
**Release Date: December 2, 2016**

*General Update*

1. Revised VBA code for Reservoir Time Series worksheets to allow Evaporation on the worksheet.

CRAM 4.015
~~~~~~~~~~
**Release Date: February 23, 2016**

*Bug Fixing*

1. Fixed problem with batch simulation and GlobalScalingFactor (it doesn't need to have that used in the subroutine).

CRAM 4.014
~~~~~~~~~~
**Release Date: August 18, 2015**

*Bug Fixing*

1. Revised Code for Excel 2013 so that when it closes workbook, it doesn't lose ExcelCRAM menus (problem with Save as AddIn button under Excel 2013).




Version 3 Releases
^^^^^^^^^^^^^^^^^^

Model version 3 releases include updated compatibility with Excel 2000, 2003, and 2007.