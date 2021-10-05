# Timelog

* Project name: MQTT over QUIC
* Name: Ivan Nikitin
* GUID: 2292523n
* Supervisor name: Colin Perkins

## Guidance

* This file contains the time log for your project. It will be submitted along with your final dissertation.
* **YOU MUST KEEP THIS UP TO DATE AND UNDER VERSION CONTROL.**
* This timelog should be filled out honestly, regularly (daily) and accurately. It is for *your* benefit.
* Follow the structure provided, grouping time by weeks.  Quantise time to the half hour.

## Week 1

### 22 Sep 2021

* *0.5 hours* Setup docs git repo
* *0.5 hours* Went through moodle and guidance for the project
* *0.5 hours* Setup zotero
* *2 hours* Identified initial set of papers to read using two previously identified papers and https://www.connectedpapers.com/
* *1 hours* Read [A First Look at QUIC in the Wild](https://link.springer.com/chapter/10.1007%2F978-3-319-76481-8_19)

### 23 Sep 2021

* *2 hours* Read [Towards Securing the Internet of Things with QUIC](https://easychair.org/publications/preprint/68D2)
* *3 hours* Read [Implementation and Analysis of QUIC for MQTT](http://arxiv.org/abs/1810.07730)

### 24 Sep 2021

* *2 hours* Wrote initial project plan with outline of goals and deliverables week by week

### 25 Sept 2021

* *0.5 hours* Setting up empty git repos for dissertation and quic implementation (added as submodules to this repo)

## Week 2

### 30 Sep 2021

* *0.5 hours* Meeting with supervisor
* *0.5 hours* Aggregating meeting notes

### 1 Oct 2021

* *1 hours* Read [Attack scenarios and security analysis of MQTT communication protocol in IoT systems](https://www.researchgate.net/publication/322059897_Attack_scenarios_and_security_analysis_of_MQTT_communication_protocol_in_IoT_system)

### 2 Oct 2021

* *2.5 hours* Read [Evaluating Critical Security Issues of the IoT World: Present and Future Challenges](https://ieeexplore.ieee.org/document/8086136)

### 3 Oct 2021

* *1 hours* Read [Secure MQTT for Internet of Things (IoT)](https://ieeexplore.ieee.org/abstract/document/7280018)
* *1 hours* Skimmed [SecKit A Model-based Security Toolkit for the Internet of Things](https://www.sciencedirect.com/science/article/pii/S0167404815000887)
* *1 hours* Identified more papers on https://www.connectedpapers.com/ to do with security challenges in IoT space to further understand the potential use cases for using QUIC (e.g. encrypting headers to prevent eavesdropping attacks)
* *2 hours* Read [Internet of Things security: A survey](https://www.sciencedirect.com/science/article/abs/pii/S1084804517301455)
* *0.5 hours* Read about SDNs and check what smart grids (SG) are
* *1 hours* Read [Security Issues In Different Layers Of IoT And Their Possible Mitigation](https://www.semanticscholar.org/paper/Security-Issues-In-Different-Layers-Of-IoT-And-Singh-Mishra/353dcc248f943fd560d0475ff9ba3cc179d74c7e)
* *1 hours* Read [Cyber Security and the Internet of Things: Vulnerabilities, Threats, Intruders and Attacks](https://riverpublishers.com/journal_read_html_article.php?j=JCSM/4/1/4)
* *0.5 hours* Read about Dolev-Yao (DY) intruder model

## Week 3

### 5 Oct 2021

* *2 hours* Formalise ideas from background reading and establish objectives for project
* *1 hours* Skim code for [quiche](https://github.com/cloudflare/quiche) and [mqtt-broker](https://github.com/bschwind/mqtt-broker)
* *0.5 hours* Read through [tokio TcpStream docs](https://docs.rs/tokio/0.2.22/tokio/net/struct.TcpStream.html)
* *0.5 hours* Look through previous meeting notes and prepare for next meeting
