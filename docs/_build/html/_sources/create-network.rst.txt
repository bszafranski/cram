Creating a Network
==================

In its simplest form, a CRAM network consists of a single node with one inflow and one demand.  The inflow specifies the amount of water entering the system and the demand specifies the amount of water leaving the system.  Because CRAM enforces mass-balance, all of the flow entering through the Inflow must exit through the Demand. If the demand has been constrained to a capacity less than the Inflow flow found in one of the minor time steps the model will determine that an xxx has occured.

Most Excel CRAM models will consist of a few hundred nodes connected by a larger number of links allowing water (flow) to be delivered to many different competing demands from a variety of sources. CRAM optimizes the system to determine the most efficient use of the water given the delivery constraints (both physical and administrative). After a solution has been attained, the user may want to experiment with additional stresses, constraints, or options on the simulation network. This is a core component of CRAM - **Scenario Analysis**.

The modeling tool supports reservoirs, instream flows, decrees, and return flows which can greatly increase the complexity of models. CRAM's operation steps allow modeling of the most complext exchanges and water rights. Please read the additional information about these features to be aware of "gotchas" that you may encounter when using the Excel CRAM modeling tool.  

Adding a Node
^^^^^^^^^^^^^

Nodes are the basic building block of a CRAM network. Nodes are used to connect other network arc types (i.e., links) and help determine the potential paths for flow in the model. There are two kinds of nodes in a model.

1. General nodes are nodes that have a single instance and physical location in the model.  You can identify a general node because it will be represented by a circle with a number inside of it.  
2. Special case nodes are related to mass balance. In each CRAM model there is one mass-balance node, but in the network diagrams (see The Network Schematic) it is represented in multiple locations. However, they all represent the same node in the model. For instance an inflow arc is attached from a mass balance node, while a demand arc is attached going-to a mass balance node. Mass balance nodes in the network schematic an be identified by the MB prefix before the node number. The MB node number is irrelevant, and simply used for book keeping.

All nodes in the network maintain mass balance during every step of the solution.

To add a node to the network click on the Create Node button on the toolbar (shown below) or click on the Excel CRAM->Network->Add Object... menu item and select Node from the object type dropdown box.

.. image:: /images/add-node.png

.. image:: /images/add-node2.png

When a new node is added to the model, it is positioned as close as possible to the last cell selected on the network schematic. The node can be repositioned by bringing up the Drawing Toolbar and clicking on the arrow to move the drawing of the node. Alternatively, right-click the node, the left click to remove the pop-up menu, then place the cursor at the edge of the node to grab it and move it.

.. image:: /images/cursor.png

The following section defines the fields on the **Edit Node** dialog box.

- The Node Number is automatically assigned by Excel CRAM. Nodes can not be reused in the network.
- The Node Name is user-defined, and are most commonly left blank.
- If the Node Name is used, it must be an ASCII string (alphanumeric and/or special characters). A good example for a node name would be a stream gage name, location, or other geographic reference. 
- The Node Location fields X and Y are not currently in use in the model. They are present only for legacy Excel CRAM models and should be ignored.
- The Display Group is set to 1 by default. The display group is an advanced feature that allows the user to hide network objects (nodes, links, etc.) in the network schematic. For more on display groups, see xxx.  
- The Comment box allows the user to add any notes about the node that might be important to the design.

.. image:: /images/edit-node.png

Adding a Link
^^^^^^^^^^^^^

A link connects two nodes. It has four user configurable parameters which help determine the amount of flow passing from the "From Node" to the "To Node" in the model. The four parameters are:

1. **High:** The High parameter is the maximum amount of flow that can pass through the link in a single solution time step. Typically the default value of "Infinite" is used. However, integer values are commonly used to represent pipeline capacities. **Advanced Note:** *If the total amount of water at the From Node is greater than the sum of all High parameters on all arcs leaving that node, an infeasible solution will occur. Using the default value of infinite avoids this problem.*
2. **Low:**  The Low parameter is the minimum amount of flow that MUST pass through the link in a single solution time step. Typically the default value of "0" is used. **Advanced Note:** *If the Low is set higher than the High parameter, an infeasible solution will occur.  If the From Node for this link does not have as much flow into it as the sum of all of the Low parameters leaving that node, an infeasible solution will occur.*
3. **Priority:**  The Priority parameter helps the network to determine the relative priority of sending water through a link.  Priorities (or ranks) in the network model are additive. **Advanced Note:** *As a model becomes more complex, the additive values of different flow paths can become more complicated.*
4. **Flow:**  The flow parameter is the optimized result of a model solution. **xxx - does this refer to the flow output??**

To add a link to the network click on the Create Link button on the toolbar (shown below) or click on the Excel CRAM->Network->Add Object... menu item and select Link from the dropdown box.

.. image:: /images/add-link.png

.. image:: /images/add-link2.png

The following section defines the fields on the **Edit Link** dialog box.

- The Link Number is automatically assigned by Excel CRAM.  Link numbers can not be reused in the network.
- The Link Name is a user-defined ASCII string that povide a common name to describe the reach. It is recommended that the name be unique within the first 32 characters but this not required. The name should normally be less than 256 characters in length.
- The Offset field is not currently used in the model. It is present for legacy Excel CRAM models only and should be ignored.
- The From Node identifies the node at the upstream end of the link. **Advanced Note: xxx - what is this???** The transfer or flow, of water from this node to the node indicated by the To Node would represent a positive number.  A negative flow would indicate that water is traveling to the "From Node".
- The To Node identifies the node at the downstream end of the link. The To Node is where the flow from this link enters and mixes with all other sources (links).
- Create Time Series Sheet/Go to Time Series Data button. This button has one of two labels on it. If the link being edited does not currently have any time series data associated with it, the button will read Create Time Series Sheet. *Most links in a CRAM model DO NOT have time series data associated with them.* Clicking on the button will create a formatted worksheet in the current scenario to hold timeseries data for the link. The user will need to populate the sheet with the appropriate data.
- The High field provides a space to specify a constant maximum capacity for the link. A value provided here will last for all minor time steps in a model run unless there is a Link Time Series Data sheet to override the value. A value of "Infinite" here indicates that the link does not have a capacity limit.
- The Low field provides a space to specify a constant minimum flow for the link. A value provided here will last for all minor time steps in a model run unless there is a Link Time Series Data Sheet in the current scenario with the Low parameter specified there. **Advanced Note:** *If a negative value is used in this field, water will flow "backwards" through the link generating a negative priority for each unit of flow transferred. This should be used with caution, and it is recommended the priority value is set to zero.*
- The Priority field provides a space to enter the priority to be assigned to that link.
- The Display Group is set to 1 by default. The display group is an advanced feature that allows the user to hide network objects (nodes, links, etc.) in the network schematic. For more on display groups, see xxx.    
- The Step Sequence allows you to enter the state of the element (Open, Closed, Frozen) for each operation step. More information can be found in xxx. **Advanced Note:** *The default value is O for open. Other values should only be used by advanced users.* 
- The Comment box allows the user to add any notes about the node that might be important to the design.
- Output To Worksheet provides a list of check boxes for Link parameters that can be written to the output worksheet when the model is run. xxx update the dialog box.

.. image:: /images/edit-link.png

Adding an Inflow
^^^^^^^^^^^^^^^^

An Excel CRAM inflow is use to provide a source of water into the network to be divided up among the demands based on the total priority of routing the water from the inflow back out of the network to the mass balance node.  An inflow can be connected to any node (except a mass balance node) and will always be connected from the mass balance node.  An inflow only has one parameter, Flow.  The flow in an inflow defines both the High and the Low on the arc.  If the Flow from an inflow is not able to find a route through the network and back to the mass balance node an infeasible solution will occur.  

To add an inflow to the network click on the Create Inflow button on the toolbar (shown below) or click on the Excel CRAM->Network->Add Object... menu item and select Inflow from the dialog box that appears.


.. image:: /images/add-inflow.png

The following section defines the fields on this dialog box.


- The Inflow Number for the inflow is automatically assigned by Excel CRAM.  Inflow numbers can not be reused in the network.
- The Inflow Name is an ASCII string for the name of the inflow to help the user provide a name to describe the inflow.  We recommend that the name be unique within the first 32 characters but this not required.  The name should normally be less than 256 characters in length.
- The Offset field is not currently in use in the model and are present for legacy Excel CRAM models.  You should not need to do anything with this field.
- The To Node identifies one of the nodes at one end of the inflow.  This node is where the flow from the inflow enters and mixes with all other source at the node specified in this field.
- Create Time Series Sheet/Go to Time Series Data button.  This button has one of two labels on it.  If the inflow being edited does not currently have any Time Series data associated with it the button will read Create Time Series Sheet.  Clicking on the button will create an formatted worksheet in the current scenario to hold timeseries data for the inflow.  
- The Step Sequence specifies the operation steps to be used for this Inflow.
- The Comment box allows the designer to add any notes about the node that might be important to the design.
- The Display Group field provides a place to assign the node's display group number. This can be used to hide the node under certain network schematic display modes.  
- Output To Worksheet provides a list of check boxes for the Inflow parameter that can be written to the output worksheet when the model is run.

Adding a Demand
^^^^^^^^^^^^^^^

An Excel CRAM demand is used to route water in the network back to the Mass-Balance node. The water that passes through a demand arc is not available for use anywhere else in the network during the same time step.  You can think of a demand as the final destination of water within the network.  The capacity of a demand is determined by the High parameter while the minimum flow which must pass through a demand arc is set by the Low parameter.  A demand arc can be connected from any node except a Mass-Balance node and it is always connected to a Mass- Balance node.

To add a demand to the network click on the Create Demand button on the toolbar (shown below) or click on the Excel CRAM->Network->Add Object... menu item and select Demand from the dialog box that appears.

.. image:: /images/add-demand.png

The following section defines the fields on this dialog box.

- The Demand Number for the demand is automatically assigned by Excel CRAM. Demand numbers can not be reused in the network.
- The Demand Name is an ASCII string for the name of the demand to help the user provide a name to describe the reach.  We recommend that the name be unique within the first 32 characters but this not required.  The name should normally be less than 256 characters in length.
- The Offset field is not currently in use in the model and are present for legacy  Excel CRAM models.  You should not need to do anything with this field.
- The From Node identifies the nodes at the start of the demand.  The transfer or flow, of water from this node to the mass balance node would represent a positive number.
- Create Time Series Sheet/Go to Time Series Data button.  This button has one of two labels on it.  If the demand being edited does not currently have any Time Series data associated with it the button will read Create Time Series Sheet. Clicking on the button will create an formatted worksheet in the current scenario to hold timeseries data for the demand.
- The High Field provides a space to specify a constant high or capacity for the demand.  A value provided here will last for all minor time steps in a model run unless there is Time Series Data to override the value.  A value of Infinite here indicates that the demand does not have a capacity limit. This can be useful for creating a demand that will take all available flow in a network.
- The Low Field provides a space to specify a constant low or minimum flow for the demand.  A value provided here will last for all minor time steps in a model run unless there is a Time Series Data sheet in the current scenario with the Low parameter specified there.  If the user sets the Low value higher than the available water in a time step an infeasible solution will occur.
- The Priority Field provides a space to enter the priority to be assigned to that demand.
- The Display Group field provides a place to assign the node's display group number. This can be used to hide the node under certain network schematic display modes.  
- The Step Sequence allows you to enter the state of the element (Open, Closed, Frozen) for each operation steps.
- The Comment box allows the designer to add any notes about the node that might be important to the design.
- Output To Worksheet provides a list of check boxes for Demand parameters that can be written to the output worksheet when the model is run.
