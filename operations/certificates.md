# Certificates
VerneMQ supports secure communication between clients and the broker. Certificates have a limited lifespan due to the risk of compromise over time, and as such, need to be replaced regularly to ensure the continued security of VerneMQ and the devices connected to the network. An expired certificate, might cause a security risk and also will stop devices to be able to connect and communicate with VerneMQ.

Quite often it is a necessary to replace certificates before they expire. Furthermore, replacing certificates without restarting the MQTT broker is crucial in ensuring continuous availability. Interrupting the broker can cause disruption to the communication between the devices connected to the network, leading to potential downtime and loss of data.

Replacing certificates without a restart can be done through a process called hot-swapping, which involves the replacement of an expiring or expired certificate with a new one without interrupting the service. This requires careful planning and execution to ensure that the new certificate is properly installed and configured before the old certificate expires. It is highly recommened to test and try this in an integration environment before deploying to production.

## Replacing certificates

## Hot-swap
