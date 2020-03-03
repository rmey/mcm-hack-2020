# Usage of github channel sample
Create the resources on the MCM hub cluster in the order mentioned (01 - 05), this will create two namespaces, a placementRule and a Subscription.
The placementRule creates a Rule for a cluster labelled with environment: Dev  (change it to a value that you prefere).


Known issues: There is a file called subscription.yaml in the folder, which defines the necessary path value in a config map. Using that file for the subscription will end up in a not working deployment on the target cluster.

Todo: Define an application that wraps up the complete deployment.
