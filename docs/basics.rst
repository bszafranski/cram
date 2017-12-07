Model Basics
============

CRAM is based on 2 core model componets.

- The network schematic
- User input sheet

From these two locations, the user is able to access most locations in the model.

The Network Schematic
^^^^^^^^^^^^^^^^^^^^^

The network schematic is the user interface for CRAM, which stores the links and nodes that represent the system. This includes inflows, reservoirs, demands, return flows, and groundwater use. Click the image below for a full resolution image.

.. image:: /images/network-schematic.png
   :scale: 100%
   :alt: CRAM Demo Model Network Schematic
   :align: center
   
The network schematic is an interactive interface for building the model and editing model parameters. For instance, clicking on Link 26 opens a pop-up that gives the link name, how it's connected (from node, to node), and what types of output it should have. This is shown in the image provided below.

.. image:: /images/interactive-interface.png


The User Input Sheet
^^^^^^^^^^^^^^^^^^^^

The user input sheet contains the user setting for a model. This allows the user to run the model, set model parameters, and show additional model details to name a few. The complexity of this sheet is dependent on the complexity of the model. 

.. image:: /images/level-of-detail.png

CRAM Sheets
^^^^^^^^^^^
These are the types of sheets used in the CRAM model. They have been broken into basic or common sheets and advanced sheets for advanced model users.

**Basic Controls:**

+-----------------------------------+-------------------------------------------------------------------------+
| Sheet Name                        |  Description                                                            |
+===================================+=========================================================================+
| User Controls                     |  Contains settings for the model, most recent run.                      |
+-----------------------------------+-------------------------------------------------------------------------+
| Network Schematic                 |  Contains the Network diagram                                           |
+-----------------------------------+-------------------------------------------------------------------------+
| Worksheet Output Template         | Contains list of elements to export to output file.                     |
+-----------------------------------+-------------------------------------------------------------------------+
| Worksheet Dictionary              | Controls sheet visibility.                                              |
+-----------------------------------+-------------------------------------------------------------------------+
| Model Workbook Version History    | Worksheet to track changes to model workbook. Manually updated by users.|
+-----------------------------------+-------------------------------------------------------------------------+
| Output Sheet                      | Worksheet to store model results for model run. CRAM raw output.        |
+-----------------------------------+-------------------------------------------------------------------------+

**Advanced Controls:**

+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| Sheet Name                        |  Description                                                                                                            |
+===================================+=========================================================================================================================+
| Global Data Sheet                 |  Contains settings for ExcelCRAM model, global variables for model execution, most recent run and dialog box settings.  |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| Node Sheet                        |  Contains text data used in node dialog box.                                                                            |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| Link Sheet                        | Contains text data used in link dialog box.                                                                             |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| Inflow Sheet                      | Contains text data used in inflow dialog box.                                                                           |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| Demand Sheet                      | Contains text data used in demand dialog box.                                                                           |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+
| Reservoir Sheet                   | Contains text data used in reservoir dialog box.                                                                        |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+

What Is CRAM?
^^^^^^^^^^^^^

Excel CRAM networks are constructed from several types of active elements, connected by nodes.  There are 6 types of active elements: Links, Inflows, Demands, Decrees, Return Flows and Reservoirs.

Water enters the network through inflows. Like a real system, all the water that enters the system plus any change in storage at reservoirs in the system must be equal to outflows (such as through demands or links that represent river reaches that leave the study area) and losses (such as evaporation or losses to groundwater.) Excel CRAM automatically enforces mass balance.

When Excel CRAM solves the network, it supplies water first to those elements with the highest numerical priority, subject to any constraints, such as physical availability and capacity constraints. This makes Excel CRAM highly suitable for analyzing systems where water rights must be administered in priority, or operations involve prioritized targets.
