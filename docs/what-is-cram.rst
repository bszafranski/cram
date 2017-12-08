What Is CRAM
============

Excel CRAM networks are constructed from several types of active elements, connected by nodes.  There are 6 types of active elements: Links, Inflows, Demands, Decrees, Return Flows and Reservoirs.

Water enters the network through inflows. Like a real system, all the water that enters the system plus any change in storage at reservoirs in the system must be equal to outflows (such as through demands or links that represent river reaches that leave the study area) and losses (such as evaporation or losses to groundwater.) Excel CRAM automatically enforces mass balance.

When Excel CRAM solves the network, it supplies water first to those elements with the highest numerical priority, subject to any constraints, such as physical availability and capacity constraints. This makes Excel CRAM highly suitable for analyzing systems where water rights must be administered in priority, or operations involve prioritized targets.

Applications
^^^^^^^^^^^^

CRAM is used by many cities, states and agencies throughout the United States for their water resources modeling and decision-making. Some typical applications include:

- Simulate municipal water supply
- Evaluate changes in water demand
- Evaluate the effects of capital improvement projects
- Water allocation by water rights (prior appropriation)
- Evaluate climate change scenarios
- Manage water use within a watershed
- Evaluate water rights
- Simulate water resources facilities and their operations

Features
^^^^^^^^

- Interactive user interface
- Reservoir operations
- Trans-basin diversions
- Minimum flow requirements
- Return flows
- Groundwater
- Advanced “What-If” scenario analysis capabilities

Under the Hood
^^^^^^^^^^^^^^

CRAM optimizes systems while preserving mass balance using what is known as a circulating network. It solves the minimum-cost flow problem using the Out-of-Kilter algorithm, where flows (or some quantity) are solved for while minimizing costs.

CRAM runs within Excel, utilizing its graphics, spreadsheets and VBA code to create a familiar user interface.


