.. _CreateNetwork-label:

Creating a Network
==================

In its simplest form, a CRAM network consists of a single node with one inflow and one demand.  The inflow specifies the amount of water entering the system and the demand specifies the amount of water leaving the system.  Because CRAM enforces mass-balance, all flow entering through the Inflow must exit through the Demand. If the demand has been constrained to a capacity less than the Inflow flow found in one of the minor time steps the model will determine that an infeasible solution has occurred. 

.. image:: /images/CreateNetwork/basic-network.png
   :align: center

Most CRAM models will consist of a few hundred nodes connected by a larger number of links allowing water (flow) to be delivered to many different competing demands from a variety of sources. CRAM optimizes the system to determine the most efficient use of the water given the delivery constraints (both physical and administrative). After a solution has been attained, the user may want to experiment with additional stresses, constraints, or options on the simulation network. This is a core component of CRAM's scenario analysis.  

.. image:: /images/CreateNetwork/complex-network.png
   :align: center
   :scale: 60%

The modeling tool supports reservoirs, instream flows, decrees, and return flows which can greatly increase the complexity of models. CRAM's operation steps allow modeling of the most complex exchanges and water rights. Please read the additional information about these features to be aware of "gotchas" that you may encounter when using the CRAM modeling tool. 

.. note:: The blue note boxes provide tips that may be helpful in avoiding modeling errors such as creating infeasible solutions.
 

Adding a Node
^^^^^^^^^^^^^

Nodes are the basic building block of a CRAM network. Nodes are used to connect other network arc types (e.g., links, inflows, demands) and help determine the potential paths for flow in the model. There are two kinds of nodes in a model.

1. General nodes are nodes that have a single instance and physical location in the model. These are the types of nodes added to the model by the user. General nodes can be identified by a circle with a number inside of it.  
2. Special case nodes are related to mass balance. In each CRAM model there is one mass-balance node, but in the network diagrams (see :ref:`NetworkSchematic-label`) it is represented in multiple locations. However, they all represent the same node in the model. For instance, an inflow arc is attached from a mass balance node, while a demand arc is attached going-to a mass balance node. Mass balance nodes in the network schematic can be identified by the MB prefix before the node number. The MB node number is irrelevant, and simply used for book keeping. These are automatically added to a model network as needed by CRAM. 

All nodes in the network maintain mass balance during every step of the solution.

.. image:: /images/CreateNetwork/node-types.png
   :scale: 75%
   :align: center
   :alt: two types of nodes in network
   
To add a node to the network, click on the Create Node button on the toolbar (shown below) or click on the menu ExcelCRAM->Network->Add Object... menu item and select Node from the object type drop-down box.

.. image:: /images/CreateNetwork/add-node.png

.. image:: /images/CreateNetwork/add-node2.png


Node Basics
~~~~~~~~~~~

The basic features necessary to add a model node are discussed in this section. Here we step through the fields on the **Edit Node** dialog box.

.. image:: /images/CreateNetwork/edit-node.png

The **Node Number** is automatically assigned by CRAM. Nodes cannot be reused in the network.

**The Node Name** is user-defined and is typically left blank. If the Node Name is used, it must be an ASCII string (alphanumeric and/or special characters). A good example for a node name would be a stream gage name, location, or other geographic reference.
 
The **Comment** box allows the user to add any notes about the node that might be important to the design.

Advanced Node Setup
~~~~~~~~~~~~~~~~~~~

- The Display Group is set to "1" by default. The display group is an advanced feature that allows the user to hide network objects (nodes, links, etc.) in the network schematic. For more on display groups, see :ref:`details-label` documentation.  


Adding a Link
^^^^^^^^^^^^^

A link connects two nodes. It has four user configurable parameters which help determine the amount of flow passing from the "From Node" to the "To Node" in the model. The four parameters are:

.. image:: /images/CreateNetwork/link-image.png
   :scale: 75%
   :align: center
   :alt: image of network link
   
1. **High:** The High parameter is the maximum amount of flow that can pass through the link in a single solution time step. Typically, the default value of "Infinite" is used. However, integer values are commonly used to represent pipeline capacities. 

.. note:: **Advanced Note:** *If the total amount of water at the From Node is greater than the sum of all High parameters on all arcs leaving that node, an infeasible solution will occur. Using the default value of "infinite" avoids this problem.*

2. **Low:**  The Low parameter is the minimum amount of flow that MUST pass through the link in a single solution time step. Typically, the default value of "0" is used. 

.. note:: *If the Low is set higher than the High parameter, an infeasible solution will occur.  If the From Node for this link does not have as much flow into it as the sum of all the Low parameters leaving that node, an infeasible solution will occur.*

3. **Priority:**  The Priority parameter helps the network to determine the relative priority of sending water through a link.  Priorities (or ranks) in the network model are additive. 

.. note:: *As a model becomes more complex, the additive values of different flow paths can become more complicated.*

4. **Flow:**  The flow parameter is the optimized result of a model solution. The user is unable to change this value - it is model output only.

To add a link to the network, click on the Create Link button on the toolbar (shown below) or click on the menu ExcelCRAM->Network->Add Object... menu item and select Link from the drop-down box.

.. image:: /images/CreateNetwork/add-link.png

.. image:: /images/CreateNetwork/add-link2.png

Link Basics
~~~~~~~~~~~

The basic features necessary to build a model link are discussed in this section. Here we step through the fields on the **Edit Link** dialog box.

.. image:: /images/CreateNetwork/edit-link.png

The **Link Number** is automatically assigned by CRAM.  Link numbers cannot be reused in the network.

The **Link Name** is a user-defined ASCII string that provides a common name to describe the reach. It is recommended that the name be unique within the first 32 characters, but this not required. The name should normally be less than 256 characters in length.

The **From Node** identifies the node at the upstream end of the link. 

The **To Node** identifies the node at the downstream end of the link. The To Node is where the flow from this link enters and mixes with all other sources (links).

**Create Time Series Sheet/Go to Time Series Data** button. This button has one of two labels on it. If the link being edited does not currently have any time series data associated with it, the button will read Create Time Series Sheet. Clicking on the button will create a formatted worksheet in the current scenario to hold time series data for the link. The user will need to populate the sheet with the appropriate data.

.. note:: *Most links DO NOT have time series data associated with them. Links used to build advanced reservoirs are an exception to this.* 

The **High** field provides a space to specify a constant maximum capacity for the link. A value provided here will last for all minor time steps in a model run unless there is a Link Time Series Data sheet to override the value. A value of "Infinite" here indicates that the link does not have a capacity limit.

The **Low** field provides a space to specify a constant minimum flow for the link. A value provided here will last for all minor time steps in a model run unless there is a Link Time Series Data Sheet in the current scenario with the Low parameter specified there.

.. note:: *If a negative value is used in this field, water will flow "backwards" through the link generating a negative priority for each unit of flow transferred. This should be used with caution, and it is recommended the priority value is set to zero.*

The **Priority** field provides a space to enter the priority to be assigned to that link.

The **Comment** box allows the user to add any notes about the node that might be important to the design.

Advanced Link Setup
~~~~~~~~~~~~~~~~~~~

- The Display Group is set to "1" by default. The display group is an advanced feature that allows the user to hide network objects (nodes, links, etc.) in the network schematic. For more on display groups, see :ref:`details-label` documentation.    
- The Step Sequence allows you to enter the state of the element (Open, Closed, Frozen) for each operation step. More information can be found in :ref:`details-label` documentation. 

.. note:: *The default value is "O" for open. Other values should only be used by advanced CRAM users.*
 
- Output To Worksheet provides a list of check boxes for Link parameters that can be written to the output worksheet when the model is run.



Adding an Inflow
^^^^^^^^^^^^^^^^

Inflows provide the source of water for an CRAM network. Once in the model the water (flow) is divided up among the demands based on the total priority of routing, from the inflow to the bottom of the network. Behind the scenes, the model "circulates" the water using the mass balance nodes. 

- An inflow can be connected TO any node (except a mass balance node)
- An inflow will always be connected FROM the mass balance node

.. image:: /images/CreateNetwork/inflow-image.png
   :scale: 65%
   :align: center
   :alt: inflow connected to a node

Inflows only have one parameter, Flow.  For Inflows, the Flow defines both the High and the Low on the arc. If the Flow from an inflow is not able to find a route through the network and back to the mass balance node an infeasible solution will occur.  

To add an inflow to the network, click on the Create Inflow button on the toolbar (shown below) or click on the menu ExcelCRAM->Network->Add Object... menu item and select Inflow from the dialog box that appears.


.. image:: /images/CreateNetwork/add-inflow.png

.. image:: /images/CreateNetwork/add-inflow2.png

Inflow Basics
~~~~~~~~~~~~~

The basic features necessary to add model inflows are discussed in this section. Here we step through the fields on the **Edit Inflow** dialog box.

.. image:: /images/CreateNetwork/edit-inflow.png

The **Inflow Number** is automatically assigned by CRAM.  Inflow numbers cannot be reused in the network.

The **Inflow Name** is a user-defined ASCII string that provides a familiar name to describe the inflow. *Inflows are ALWAYS named by users within the model.* We recommend that the name be unique within the first 32 characters, but this not required.  The name should normally be less than 256 characters in length.

The **To Node** identifies the node at the receiving end of the inflow.  The To Node is where the flow from the inflow enters and mixes with all other sources (links or inflows).

**Create Time Series Sheet/Go to Time Series Data** button. This button has one of two labels on it. If the inflow being edited does not currently have any time series data associated with it the button will read Create Time Series Sheet.  Clicking on the button will create a formatted worksheet in the current scenario to hold time series data for the link. The user will need to populate the sheet with the appropriate data.

.. note:: *Inflows should always have time series data associated with them. Failure to create a Time Series Sheet will result in a zero inflow.*

The Comment box allows the user to add any notes about the node that might be important to the design.

Advanced Inflow Setup
~~~~~~~~~~~~~~~~~~~~~

- The Step Sequence specifies the operation steps to be used for this Inflow. More information can be found in :ref:`details-label` documentation. 

.. note:: *The default value is "O" for open. Other values should only be used by advanced CRAM users.*

- The Display Group is set to "1" by default. The display group is an advanced feature that allows the user to hide network objects (nodes, links, etc.) in the network schematic. For more on display groups, see :ref:`details-label` documentation.  
- Output To Worksheet provides a list of check boxes for the Inflow parameter that can be written to the output worksheet when the model is run.

Adding a Demand
^^^^^^^^^^^^^^^

Demands are used to route water to specific users in the CRAM network (e.g., cities, farmers, ditches). The water that passes through a demand arc is not available for use anywhere else in the network during the same time step.  Demands can be thought of as the final destination of water within the network.  

The capacity of a demand is determined by the High parameter while the minimum flow that must pass through a demand arc is set by the Low parameter.

- A demand can be connected FROM any node (except a Mass-Balance node)
- A demand is always connected TO a mass balance node

.. image:: /images/CreateNetwork/demand-image.png
   :scale: 65%
   :align: center
   :alt: demand connected from a node

To add a demand to the network, click on the Create Demand button on the toolbar (shown below) or click on the menu ExcelCRAM->Network->Add Object... menu item and select Demand from the dialog box that appears.

.. image:: /images/CreateNetwork/add-demand.png

.. image:: /images/CreateNetwork/add-demand2.png

Demand Basics
~~~~~~~~~~~~~

The basic features necessary to add model demands are discussed in this section. Here we step through the fields on the **Edit Demand** dialog box.

.. image:: /images/CreateNetwork/edit-demand.png

The **Demand Number** is automatically assigned by CRAM. Demand numbers cannot be reused in the network.

The **Demand Name** is a user-defined ASCII string that provides a familiar name to describe the demand. *Demands are ALWAYS named by users within the model.* We recommend that the name be unique within the first 32 characters, but this not required. The name should normally be less than 256 characters in length.

The **From Node** identifies the node at the upstream or distributing side of the demand.

**Create Time Series Sheet/Go to Time Series Data** button. This button has one of two labels on it. If the demand being edited does not currently have any Time Series data associated with it the button will read Create Time Series Sheet. Clicking on the button will create a formatted worksheet in the current scenario to hold time series data for the link. The user will need to populate the sheet with the appropriate data.

.. note:: *Demands should always have time series data associated with them. Failure to create a Time Series Sheet will result in the demand having a default value of infinite.*

The **High** field provides a space to specify a constant maximum capacity for the demand. A value provided here will last for all minor time steps in a model run unless there is Demand Time Series Data Sheet to override the value. A value of "Infinite" here indicates that the demand does not have a capacity limit. This can be useful for creating a demand that will take all available flow in a network.

The **Low** field provides a space to specify a constant minimum flow for the demand. A value provided here will last for all minor time steps in a model run unless there is a Demand Time Series Data Sheet in the current scenario with the Low parameter specified there. 

.. note:: *If the user sets the Low value higher than the available water in a time step an infeasible solution will occur. Non-zero low values should be used sparingly.*

The **Priority** field provides a space to enter the priority assigned to that demand.

Advanced Demand Setup
~~~~~~~~~~~~~~~~~~~~~

- The **Display Group** is set to "1" by default. The display group is an advanced feature that allows the user to hide network objects (demands, links, etc.) in the network schematic. For more on display groups, see :ref:`details-label` documentation. 

- The **Step Sequence** allows the user to enter the state of the element (Open, Closed, Frozen) for each operation step.

.. note:: *The default value is "O" for open. Other values should only be used by advanced CRAM users.*

- The **Comment** box allows the user to add any notes about the node that might be important to the design.

- **Output To Worksheet** provides a list of check boxes for Demand parameters that can be written to the output worksheet when the model is run.


Adding a Reservoir
^^^^^^^^^^^^^^^^^^

A CRAM Reservoir is used to simulate the storage of water in a reservoir. This network object may be used to represent either surface or groundwater storage systems. Reservoirs can be built to include complex operations such as hydropower, water rights exchanges, flood storage and dead storage.  

To add a reservoir to the network, click on the Create Reservoir button on the toolbar (shown below) or click on the menu ExcelCRAM->Network->Add Object... menu item and select Reservoir from the dialog box that appears.

.. image:: /images/CreateNetwork/add-reservoir.png

.. image:: /images/CreateNetwork/add-reservoir2.png

Reservoir Basics
~~~~~~~~~~~~~~~~

The basic features necessary to add reservoirs are discussed in this section. Here we step through the fields on the **Edit Reservoir** dialog box.

.. image:: /images/CreateNetwork/edit-reservoir.png

The **Reservoir Number** is automatically assigned by CRAM. Reservoir numbers cannot be reused in the network.

The **Reservoir Name** is a user-defined ASCII string that provides a familiar name to describe the reservoir. *Reservoirs are ALWAYS named by users within the model.* We recommend that the name be unique within the first 32 characters, but this not required. The name should normally be less than 256 characters in length.

The **From Node** identifies the node at the upstream or distributing side of the reservoir.

The **To Node** identifies the node at the downstream end of the reservoir.  This node is where the flow stored by the reservoir in the previous time step (Minor Time Step) is released back to the network. A link from this node to the From Node will allow the reservoir to retain storage from one time step (Minor Time Step) to another.

**Create Time Series Sheet/Go to Time Series Data** button. This button has one of two labels on it. If the reservoir being edited does not currently have any Time Series data associated with it the button will read Create Time Series Sheet. Clicking on the button will create a formatted worksheet in the current scenario to hold time series data for the link. The user will need to populate the sheet with the appropriate data.

.. note:: *Reservoirs usually do not have time series data associated with them. However, links that are a part of the reservoir, such as those used to represent target storage, usually do have time series data.*

The **Dead Storage** is currently inactive.

The **Active Storage** is currently inactive.

The **Total Capacity** provides a place to record the total storage capacity of the reservoir. This can be either active storage or total storage depending on how you have decided to model the reservoir.

.. note:: *The Total Capacity must be less than or equal to the maximum value added to the reservoir elevation-area-volume curve (data).*

The **Initial Contents** provides a place to record the initial storage contents of the reservoir. This can be a variety of values (including zero), depending on how the reservoir is modeled.

The **Volume-Area Curve** contains pairs of numbers that describe the volume-area relationship for the reservoir.  This table of numbers is used to calculate average surface area over a time step (minor time step) to calculate evaporation. The numbers for this field are entered in increasing order from the lowest volume to the reservoir's total capacity with the corresponding area following the colon. (i.e.  0:0, 100:40, 200:60 would represent a reservoir that had covered 40 acres when it contained 100 acre-feet (AF) and covered 60 acres when it contained 200 AF). Values between the points are linearly interpolated to determine volume and surface area. Using the previous example, 150 AF of water would correspond to 50 acres in surface area.

.. note:: *The reservoir elevation-volume curve must start with a data point of 0 elevation, 0 storage (e.g., 0 ft, 0 af). If this value is missing, it will cause errors in the calculation of reservoir evaporation.*

The **Seasonal Evaporation Rate Series** stores the evaporation rates as a series of comma delimited numbers. There should be one value for each minor time step in your model. 

.. note:: *There are 2 options for evaporation data. 1. Time series of reservoir evaporation (by Minor Time Step). 2. Annual repeating evaporation values (by Minor Time Step).*

Advanced Reservoir Setup
~~~~~~~~~~~~~~~~~~~~~~~~

- The **Display Group** is set to "1" by default. The display group is an advanced feature that allows the user to hide network objects (demands, links, reservoirs, etc.) in the network schematic. For more on display groups, see :ref:`details-label` documentation. 

- The **Comment** box allows the user to add any notes about the node that might be important to the design.

- **Output To Worksheet** provides a list of check boxes for Reservoir parameters that can be written to the output worksheet when the model is run.



Adding an Instream Flow
^^^^^^^^^^^^^^^^^^^^^^^

A CRAM Instream Flow is a specialized object used in model to simulate water rights that are used to keep water in the stream and make them available below the instream flow for diversion without increasing the priority of the demands below the instream flow.  

To add an instream flow to the network, click on the "Create an Instream Flow" button on the toolbar (shown below) or click on the menu ExcelCRAM->Network->Add Object... menu item and select Reservoir from the dialog box that appears.

.. image:: /images/CreateNetwork/add-instream-flow.png

.. image:: /images/CreateNetwork/add-instream-flow2.png

Instream Flow Basics
~~~~~~~~~~~~~~~~~~~~

The basic features necessary to add instream flow objects are discussed in this section. Here we step through the fields on the **Edit Instream Flow** dialog box.

.. image:: /images/CreateNetwork/edit-instream-flow.png

The **ISF Number** is automatically assigned by CRAM. Instream flow numbers cannot be reused in the network.

The **ISF Name** is a user-defined ASCII string that provides a familiar name to describe the instream flow. *ISFs are ALWAYS named by users within the model.* We recommend that the name be unique within the first 32 characters, but this not required. The name should normally be less than 256 characters in length.

The **From Node** identifies the node at the upstream or distributing side of the instream flow.

The **To Node** identifies the node at the downstream end of the instream flow.  This node is where the flow from the instream flow re-enters the network and mixes with all other sources at the node specified in this field.

**Create Time Series Sheet/Go to Time Series Data** button. This button has one of two labels on it. If the instream flow being edited does not currently have any Time Series data associated with it, the button will read Create Time Series Sheet. Clicking on the button will create a formatted worksheet in the current scenario to hold time series data for the link. The user will need to populate the sheet with the appropriate data.

.. note:: *Instream flows have time series data associated with them depending on their complexity. For instance, if the instream flow varies over time, then the user should create corresponding time series data. However, if the instream flow is constant, a single value within the **High** parameter field is sufficient.*

The **High** field provides a space to specify a target or goal for the instream flow.  A value provided here will last for all minor time steps in a model run unless there is Time Series Data to override the value.  **Do not leave the high value to Infinite!**  The High field for this network element represents the "minimum" amount of water that the instream flow should try to preserve in the river.  Excess flow capabilities of the river at this location should be represented by a standard model link (with zero priority) set in parallel with the instream flow object. Thus, the sum of the two parallel arcs (1 instream flow and 1 link) will represent the total flow through the river.

.. note:: *Do not set the High value to Infinite, or else the model will try and route all available water through the instream flow object.* 

The **Low** field provides a space to specify a constant minimum flow for the instream flow. A value provided here will last for all minor time steps in a model run unless there is a Instream Flow Time Series Data Sheet in the current scenario with the Low parameter specified there. Since the instream flow is already trying to attain the value set as a **High**, it is unnecessary to change the Low from zero. 

.. note:: *An instream flow Low should always be set to zero (0). An infeasible solution will likely occur otherwise.*

The **Priority** field provides a space to enter the priority assigned to that instream flow.

**Best Practices:** The instream flow should be setup with a single link above it and a single link downstream of it. In the middle, there are two parallel arcs, an instream flow and a link. This helps to avoid confusion regarding the link priorities. The total flow of a river reach (sum of instream flow and its parallel link) is easily ascertained from next downstream link. See image below.

.. image:: /images/CreateNetwork/instream-best-practices-temp.png
 
Advanced Instream Flow Setup
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- The **Display Group** is set to "1" by default. The display group is an advanced feature that allows the user to hide network objects (demands, links, reservoirs, etc.) in the network schematic. For more on display groups, see :ref:`details-label` documentation. 

- The **Comment** box allows the user to add any notes about the node that might be important to the design.

- **Output To Worksheet** provides a list of check boxes for Instream Flow parameters that can be written to the output worksheet when the model is run.


Moving Objects in CRAM
^^^^^^^^^^^^^^^^^^^^^^

When a new node is added to the model, it is positioned as close as possible to the last cell selected on the network schematic. The node can be repositioned by bringing up the Drawing Toolbar and clicking on the arrow to move the drawing of the node. Alternatively, right-click the node, then left-click to remove the pop-up menu, then place the cursor at the edge of the node to grab it and move it.

.. image:: /images/CreateNetwork/cursor.png

