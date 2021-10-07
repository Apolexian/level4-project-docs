# Project plan for MQTT over QUIC

## Prioritisation

**Must**

* Must port MQTT implementation to use QUIC
  * This is the essence of the project and all evaluation would not be possible without this
* Must evaluate ported Rust implementation versus existing MQTT TCP implementations (mosquitto) and MQTT QUIC C implementation presented in `Implementation and Analysis of QUIC for MQTT - Puneet Kumar (2019)` in terms of binary size, stack size, heap size, latency
  * Making the port as efficent as existing implementations is important in order to make the solution usable
  * Measuring binary size, stack and heap allocations is both important for hardware constrained devices and to evaluate Rust for embedded/systems programming
  * This evaluation will be the base measure for further thinning down of the implementation
* Must show that combination of authentication and encryption of headers and payload can guarantee data integrity
  * This is the primary usecase due to QUIC encrypted headers
  * This will also be the basis to establishing why a cryptography scheme/suite is needed for the underlying protocol for MQTT
  * Attack type is presented in `Attack scenarios and security analysis of MQTT communication protocol in IoT systems - Syaiful Andy (2017)`

**Should**

* Should evaluate different methods of thinning down QUIC and MQTT in order to use them on hardware constrained resources and thin down both implementations
  * Some methods presented in `Towards Securing the Internet of Things with QUIC - Lars Eggert (2020)`
  * Evaluating if these methods are reproducable for a Rust QUIC implementation would possibly provide a path to a general framework for thinning down protocols for IoT
  * Important to thin down the implementation in order for solution to be viable for hardware constrained devices
  * This will be the basis of evalutaion of the overhead of TLS
* Should evaluate the overhead of TLS and compare it to KP-ABE in terms of overhead and feature set
  * Important as TLS will be the main overhead to address for the system, however its features are required for providing data integrity
  * A comparison is presented in `Secure MQTT for Internet of Things (IoT) - Meena Singh (2015)`, however this comparison is made not in the context of TLS for QUIC. This comparison will be made in terms of size overhead and feature-fullness.

**Could**

* Could extend QUIC to use KP-ABE and port implementation to use this instead of TLS
  * An extension that allows the use of KP-ABE could provide an alternative for hardware constrained devices
  * This however would be a large effort

**Won't have this time**

* Evaluate the performance of the ported MQTT implementation in the context of mesh networks
  * Setting up a mesh network test bench would take away too much time from the timeline of the project

## Timeline

### Semester 1

Week 3:

* Finalise plan and prioritisation
* Run quiche and mqtt as is on local

Week 4:

* Understand mqtt implementation and identify where tcp has to be replcaed
* Compare APIs of quiche and tokio::net::TcpStream to understand what changes to interfaces will need to be made

Week 5-8:

* Port mqtt to quic
* Make sure it runs on local

Week 9-10:

* Set up test bench on devices/mininet
* Set up other implementations that port will be compared to
* Create scripts for data collection during evaluation and testing

Week 11-13:

* Run the port on test benches to make sure everything works
* Evaluate performance to get the basline measurements for the port
* Recreate data integrity attack from `Attack scenarios and security analysis of MQTT communication protocol in IoT systems - Syaiful Andy (2017)` on test bench
* Evaluate resilience of port against recreated data integrity attack
* Work on status report

### Semester 2

Week 1-3:

* Thin down client
* Evaluate overhead and feature fullness of TLS vs KP-ABE
* Re-evaluate final thinned down version versus other implementations (mqtt in c, `Puneet Kumar (2019)`, original port)

Week 4-6:

* Attempt to port quic implementation to use KP-ABE
* Evaluation of resulting solution in terms of overhead

Week 7-9:

* Work on first draft of dissertation

Week 10-11:

* Work on feedback for dissertation and submission
