.. _details-label:

Model Details
=============

This section is under construction.

Model Customization Overview
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Excel CRAM provides powerful tools that allow you to develop a simulation that realistically represents your system. There are three ways to customize your model:

1. **Operation Steps:** Operation steps allow the user to interupt the network solution at each minor time step using a series of sub-timesteps which we call operations steps.  This allows for simulation of complex operations without resorting to writing computer code.
2. **User Code:** If a system's operations are too complex and can not be represent in CRAM using Operation Steps alone, a user can write code to control Excel CRAM.  This code is written in Visual Basic for Applications (VBA.)
3. **Display Groups:** A network model can become complex. Display Groups allow the user to manage that complexity by controlling the visual presentation of the model network. The user can hide network constructs such as mass balance nodes or group model objects together by type (node, link, etc.) or region. **xxx - This is old text - You can Ind6ptp3eInd6ptp3e and you can kpla6qkpla6q that can represent network constructs as a single image.**


.. _opsteps-label:

Operation Steps
^^^^^^^^^^^^^^^

Operation steps can be thought of as sub-timesteps or iterations within a timestep. CRAM models may require the use of operation steps if there are complex water rights operations. For instance, if a water right holder downstream of a reservoir owns water within the reservoir, but not the river, an operation step may need to be used to release water during an iteration of the timestep such that only the water right holder may access it. This complex water rights situation is easily modeled using CRAM's operation steps. 

When a model is first built, CRAM will prompt the user asking how many operations steps there should be. **xxx old text - If you are in the process of setting up a simulation, you will be asked how many op steps your model should have. xxx**  When this is setup, CRAM will automatically initialize the operations steps for each element in the Open (O) state.

If modifying an existing simulation, the Operation Step Manager must be used to access model operation steps. The Operation Step Manager is accessible through the Excel CRAM menu as shown in the image below. The Operation Step Manager allows the user to insert a new operation step or delete an existing operation step. If choosing to insert a new operation step the user will be given the opportunity to copy data from the element settings for an existing operation step. This saves the time of entering steps for each element. Often, a new operation step will be incrementally different from a previous step, so it is quite helpful to use this ability to copy an existing operation step and then make the necessary changes to the steps for individual components.

.. image:: /images/op-step-manager.png
   :scale: 100%
   :align: center


User Code
^^^^^^^^^

The VBA code can be used to check and changes values in the model while it is running. These functions intercept the execution of the model at various points to allow the use of macros from the main Excel CRAM program to change values in the current solution step. There are two Excel CRAM macros that are the primary focus of these routines.

**GetParameter()**

The GetParameter macro function is used to check the current value of a parameter of a network element at the current state of the model. The value returned by GetParameter is dependent on the Event or Subroutine from which it is called. An example call to the GetParameter macro is:

 xxx-szLink1Flow = Application.Run(GET_PARAMETER, "Link", 1, "Flow")

In this example, the return value **xxx-szLink1Flow** is filled with the current value for the Flow in the network element Link 1.

xxx to be continued xxx


Display Groups
^^^^^^^^^^^^^^

The dialog box below displays the current status of Display Groups on your Network Schematic worksheet. By default all Display Groups are visible but by selecting one of them and then clicking on the appropriate arrow button you can change the status of a Display Group from visible to invisible and back again. Click the Redraw Network button to see your changes. Clicking the Rename Group button allows you to change the name and description of the Display Group from the default value of Display Group n description goes here.

.. image:: /images/display-group-manager.png
   :align: center

Navigate to the Display Groups from the ExcelCRAM menu as shown below.

.. image:: /images/edit-display-groups.png
   :align: center
