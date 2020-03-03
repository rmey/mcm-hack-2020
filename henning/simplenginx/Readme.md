# Usage of github channel sample
Create the resources on the MCM hub cluster in the order mentioned (01 - 05), this will create two namespaces, a placementRule and a Subscription.
The placementRule creates a Rule for a cluster labelled with environment: Dev  (change it to a value that you prefere).

The subscription, currently is written in that way, that it assumes the deployables in the path henning/simplenginx/deployables that means: the definition of the github repo works in that way, that the channel defines the root path of the repo and it is necessary to add the path on the same level as the channel resource. This is set to the path where the deployables can be found. In this case henning/simplenginx/deployables


Known issues: There is a file called subscription.yaml in the folder, which defines the necessary path value in a config map. Using that file for the subscription will end up in a not working deployment on the target cluster.

Todo: Define an application that wraps up the complete deployment.
