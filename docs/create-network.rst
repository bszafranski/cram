Creating a Network
==================

In its simplest form, an Excel CRAM network consists of a single node with one inflow and one demand.  The inflow specifies the amount of water entering the system and the demand specifies the amount of water leaving the system.  Because Excel CRAM enforces mass-balance all of the flow entering through the Inflow must exit through the Demand.  If the demand has been constrained to a capacity less than the Inflow flow found in one of the minor time steps the model will determine that an Indch_kouIndch_kou has occured.

Most Excel CRAM models will consist of a few hundred nodes connected by a larger number of links allowing water (flow) to be delivered to many different competing demands from a variety of sources.  The problem Excel CRAM was built to solve is to help determine the most efficient use of the water given the delivery constraints (both physical and administrative) and provide the ability to experiment with additional stresses on a simulation network.

The modeling tool supports operation steps, decrees, instream flows, return flows and reservoirs which can greatly increase the complexity of models.  Please read the additional information about these features to be aware of "gotchas" that you may encounter when using the Excel CRAM modeling tool.

Adding a Node
^^^^^^^^^^^^^

Nodes are the basic building block of an Excel CRAM network.  The nodes in a network are the points where the other network arc types meet and the nodes help to determine the potential paths for transport in the model.  There are two kinds of nodes in a model.  

General nodes are nodes that have a single instance and physical location in the model.  You can identify a general node because it will be represented by a circle with a number inside of it.  

The other type of node in the model is the special case i3mzf8i3mzf8.  In each Excel CRAM model there is actually on one mass-balance node but in our network diagrams it is represented in multiple locations in the diagram but they all represent the same node in the model.  A mass balance node is added to the model whenever you add a network arc to the model that is always attached to or from a mass balance node.  The inflow arc, for example is always attached from a mass balance node.  The mass balance node representations in the model can be identified by the MB prefix before the node number.  The node number in this instance is not important since they all refer to the same node.  The node number for each instance of the mass balance node is simply a book keeping trick for the Network Schematic view.

All nodes in the network maintain mass balance during every step of the solution.

To add a node to the network click on the Create Node button on the toolbar (shown below) or click on the Excel CRAM->Network->Add Object... menu item and select Node from the object type dropdown box.

.. image:: /images/add-node.png

The node is positioned as close as possible to the last cell selected on the network schematic.  You can reposition the node by bringing up the Drawing Toolbar and clicking on the arrow to move the drawing of the node.

The following section defines the fields on this dialog box.

- The Node Number for the node is automatically assigned by Excel CRAM and nodes can not be reused in the network.
- The Node Name is an ASCII string for the name of the node to help the user understand the location they are connecting to or from when adding other network elements.  A good example for a node name would be a stream gage name or location or other geographic reference.
- The Node Location fields X and Y are not currently in use in the model and are present for legacy Excel CRAM models.  You should not need to do anything with these fields.
- The Display Group field provides a place to assign the node's display group number. This can be used to hide the node under certain network schematic display modes.  
- The Comment box allows the designer to add any notes about the node that might be important to the design.


Adding a Link
^^^^^^^^^^^^^

A link in an Excel CRAM network connects two nodes.  It has three user configurable parameters which help determine the amount of flow passing from the from node to the to node in the model. The four parameters are:


1. **High:** The high parameter is the maximum amount of flow that can pass through the link in a single solution time step.  If the total amount of water at the from node is greater than the total high parameters on all arcs leaving that node an infeasible solution will occur.
2. **Low:**  The low parameter is the minimum amount of flow that must pass through the link in a single solution time step.  If the low is set higher than the High parameter you will have an infeasible solution.  You can also get an infeasible solution if the from node for this link does not have as much flow into it as the sum of all of the low parameters leaving that node.
3. **Priority:**  The priority parameter helps the network to determine the relative priority of sending water through a link.  Priorities (or ranks) in the network model are additive.
4. **Flow:**  The flow parameter is the optimized result of a model solution.

To add a link to the network click on the Create Link button on the toolbar (shown below) or click on the Excel CRAM->Network->Add Object... menu item and select Link from the dropdown box.

.. image:: /images/add-link.png


The following section defines the fields on this dialog box.

- The Link Number for the link is automatically assigned by Excel CRAM.  Link numbers can not be reused in the network.
- The Link Name is an ASCII string for the name of the link to help the user provide a common name to describe the reach.  We recommend that the name be unique within the first 32 characters but this not required.  The name should normally be less than 256 characters in length.
- The Offset field is not currently in use in the model and are present for legacy  Excel CRAM models.  You should not need to do anything with this field.
- The From Node identifies one of the nodes at one end of the link.  The transfer or flow, of water from this node to the node indicated by the To Node would represent a positive number.  A negative flow would indicate that water is traveling to the "From Node".
- The To Node identifies one of the nodes at one end of the link.  This node is where the flow from the link enters and mixes with all other source at the node specified in this field.
- Create Time Series Sheet/Go to Time Series Data button.  This button has one of two labels on it.  If the link being edited does not currently have any Time Series data associated with it the button will read Create Time Series Sheet.  Clicking on the button will create an formatted worksheet in the current scenario to hold timeseries data for the link.
- The High Field provides a space to specify a constant high or capacity for the link.  A value provided here will last for all minor time steps in a model run unless there is Time Series Data to override the value.  A value of Infinite here indicates that the link does not have a capacity limit.
- The Low Field provides a space to specify a constant low or minimum flow for the link.  A value provided here will last for all minor time steps in a model run unless there is a Time Series Data sheet in the current scenario with the Low parameter specified there.  A negative value in this field will allow water to flow "backwards" through the link generating a negative priority for each unit of flow transferred.  This should be allowed with caution and normally a priority value of zero.
- The Priority Field provides a space to enter the priority to be assigned to that link.
- The Display Group field provides a place to assign the node's display group number. This can be used to hide the node under certain network schematic display modes.  
- The Step Sequence allows you to enter the state of the element (Open, Closed, Frozen) for each operation step.
- The Comment box allows the designer to add any notes about the node that might be important to the design.
- Output To Worksheet provides a list of check boxes for Link parameters that can be written to the output worksheet when the model is run.

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
