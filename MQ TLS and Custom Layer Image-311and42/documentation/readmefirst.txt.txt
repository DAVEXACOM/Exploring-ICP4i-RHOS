PART 1 of the document – this is simply showing how to create a custom layer on the MQ Image and make it available in an RHOS 3.11 cluster with ICP4i and connect administration tools over a specific SVRCONN channel. This section provides a comprehensive set of steps for creating custom images.

PART 2 of the document – this builds to connecting to queue managers on RHOS 4.2 over TLS from your laptop. It takes the custom image approach, which although valid is not preferred approach to enable TLS for off cluster client connect for applications and tools. See PART 3 for the preferred approach. 
This section provides a comprehensive set of steps for creating custom images in general. It also captures in detail the steps for setting up TLS for any client/server pair.
a)	Setting up TLS between a client connected tools on the lap top to a queue manager running natively on your laptop
b)	Reusing the collateral in a) above to build a custom docker image/container and have client connect tools on the lap top connect over TLS to a queue manager in the container running on the laptop.
c)	Push the custom image to dockerhub, use an image stream on RHOS 3.11 to pull the image onto RHOS 3.11 cluster. ICP4i (Helm) deploy of the custom image. Connect tools on the lap top to the queue manager on ICP4i on RHOS 3.11 via TLS
d)	Push the custom image to dockerhub, use an image stream on RHOS 4.2 to pull the image onto RHOS 4.2 cluster. ICP4i (Helm) deploy of the custom image. Connect tools on the lap top to the queue manager on ICP4i on RHOS 4.2 via TLS

PART 3 of the document – this captures the preferred approach of enabling TLS connectivity for off-cluster client applications and tools. The preferred method passes in the keys and cert files as part of the Helm deployment.
Additionally, this approach does not require a custom image. It uses a modified version of the ICP4i MQ Helm charts and a Kubernetes configMap to house an MQSC file that allows a unique channel name (based off a naming convention that leverages the Queue Manager) to be created at Helm release time when the queue manager is specific. Therefore, no requirement for a custom image per queue manager per cluster. 
