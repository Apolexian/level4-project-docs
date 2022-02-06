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

* *0.5 hours* Set up empty git repos for dissertation and quic implementation (added as submodules to this repo)

## Week 2

### 30 Sep 2021

* *0.5 hours* Meeting with supervisor
* *0.5 hours* Aggregated meeting notes

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

* *2 hours* Formalised ideas from background reading and establish objectives for project
* *1 hours* Skim code for [quiche](https://github.com/cloudflare/quiche) and [mqtt-broker](https://github.com/bschwind/mqtt-broker)
* *0.5 hours* Read through [tokio TcpStream docs](https://docs.rs/tokio/0.2.22/tokio/net/struct.TcpStream.html)
* *0.5 hours* Look through previous meeting notes and prepare for next meeting

### 6 Oct 2021

* *0.5 hours* Finished prep for the meeting
* *0.5 hours* Supervisor meeting
* *2 hours* Created [Prioritisation of ideas for the project using MoSCoW](./plan.md)
* *1 hours* Created [Rough timeline for project](./plan.md)

### 8 Oct 2021

* *1 hours* Went through [mininet walkthrough](http://mininet.org/walkthrough/) and ran simple http server on a basic topology
* *0.5 hours* Look through vagrant docs and install it
* *1 hours* Set up vagrantfile
* *2 hours* Tried to run the quiche example using simple mininet two host topology but encountering errors: network is unreachable and failed to process packet: -10

### 9 Oct 2021

* *3 hours* Fixed bugs in mininet script, updated mininet to use python3, set up script to use threads to connect 3 clients in parallel to server, tested script using wireshark, updated some parameters in vagrantfile

## Week 4

### 13 Oct 2021

* *0.5 hours* Meeting with supervisor
* *0.5 hours* Aggregated meeting notes

### 15 Oct 2021

* *2.5 hours* Wrote up the prioritisation and motivation with more discussion from the plan to the status report

### 17 Oct 2021

* *0.5 hours* Researched generating TLS certificates that are needed for mqtt broker example and wrote script to create them
* *1.5 hours* Modified code from [rumqtt examples](https://github.com/bytebeamio/rumqtt) to run example mqtt client and broker (pre-port version) on local and verified packets via wireshark
* *1 hours* Changed [quic test code](https://github.com/Apolexian/level4-scripts/blob/master/quic/quic-mininet.py) to use a dumbbell topology and fixed some cmake issues in the vagrantfile
* *1.5 hours* Made script to run rumqtt broker and server (unported) in mininet using dumbbell topology

### 18 Oct 2021

* *5 hours* [Started porting the mqtt implementation to use quiche](https://github.com/Apolexian/rumqtt). First time unsuccessful due to not being able to substitute tokio with mio (encountered too many lifetime semantics to get mio UdpSocket to work). Second time used pure tokio and compiled successfully, did not have time to fully test though.

## Week 5

### 20 Oct 2021

* *0.5 hours* Meeting with supervisor
* *0.5 hours* Aggregated meeting notes

### 21 Oct 2021

* *1 hours* Started reading interfaces and source code for tokio and underlying mio tcp socket, listener and stream to understand how to create quic counterparts
* *2.5 hours* Added QuicSocket definition and base methods for connecting as well as QuicListener definition
* *0.5 hours* Moved QuicSocket to its own repo and added some documentation for the methods so far
* *0.5 hours* Collected questions from previous meeting, formulated them and emailed Mihail

### 24 Oct 2021

* *2 hours* Added functions for send and recv to [QuicListener](https://github.com/Apolexian/QuicSocket/blob/master/src/lib.rs#L191)
* *0.5 hours* Published QuicSocket as a crate so I can have an easier time using it in my rumqtt fork

## Week 6

### 26 Oct 2021

* *3 hours* Changed QuicSocket to auto-configure a quiche config, tried initial port of rumqttd and rumqttc using QuickSocket (connects but errors out when sending), changed mqtt scripts to use ported versions of rumqtt
* *1 hours* Read [Ofcom report](https://www.ofcom.org.uk/__data/assets/pdf_file/0020/224192/uk-home-broadband-performance-technical-report-march-2021-data.pdf) to check for values I can use for link simulation in mininet. Also read some general articles about packet loss patterns.
* *0.5 hours* Checked old version of chrome to see what values are used for network speed presets in the network tab
* *1 hours* Aggregated progress, thoughts and questions for next meeting
* *1 hours* Created minimal example of usage of QuicSocket which can be used to debug it in isolation. Found a bug with the send function

### 27 Oct 2021

* *0.5 hours* Meeting with supervisor
* *0.5 hours* Aggregated meeting notes
* *1 hours* Skimmed RFCs 8593 and 8667 and found some relevant test simulation info and topology descriptions. Looked through mininet python API reference and found [link options](https://github.com/mininet/mininet/blob/master/mininet/link.py#L320) in the source code since they are not documented in the reference.
* *0.5 hours* Emailed author of `Implementation and Analysis of QUIC for MQTT` to ask for source code for the paper and Mihail to ask for report data

### 28 Oct 2021

* *2 hours* Fixed QuickListener send and recv functions and modified [test client and server](https://github.com/Apolexian/level4-scripts/tree/master/socket) so sending and receiving actually works now
* *0.5 hours* Added dissertation template to repo and made a makefile for it
* *3 hours* Started working on getting port to work, but getting Timeout error. Hard to debug but seems that the timeout is during MQTT connection establishment.

### 31 Oct 2021

* *2 hours* Debugged issue with packets and realise that quiche does not handle initial packets and handshake fully when simply establishing connection, so QuicSocket will have to do this (probably on connect/accept). Also realised that buffer was being overwritten because of this.
* *5.5 hours* Debugged further and understood quiche library more. It does **not** in fact handle handshake nor retry when connecting automatically. Instead you need to keep up the send/recv loop until the handshake is established. For some reason, none of their examples do this nor use a retry token but they work. Got as far as getting Retry packets to work in the eventloop.

## Week 7

### 2 Nov 2021

* *1 hours* Got QuicSocket to go past Retry packets to Handshake packets but get buffer errors
* *3 hours* Got handshake to work but it seems that there is an issue with the connection object. Stream send should initialse the stream for the connection, however the connection object is obviously different for server and client in my case which means that the streams never get initialised on server side. This also probably means that the connection will never receive what is sent.
* *0.5 hours* Wrote [question](https://github.com/cloudflare/quiche/issues/1077) on quiche repo about the issue
* *0.5 hours* Prep for next meetings

### 3 Nov 2021

* *0.5 hours* Meeting with supervisor
* *0.5 hours* Aggregated meeting notes
* *3 hours* Tried to get stream send a recieve working based on answer from @LParude on github. Works better now but I seem to have a bug with polling because running client twice sends data. Asked about it on the same [github issue](https://github.com/cloudflare/quiche/issues/1077)

### 6 Nov 2021

* *2 hours* Fixed stream send and socket is now able to send, although consecutive sends seems to break. Tried to use this in the MQTT port but it seems that it attempts to send before ever creating a connection which is bizarre.

## Week 8

### 10 Nov 2021

* *4 hours* Debugging why the eventloop does not trigger in the MQTT implementation

### 11 Nov 2021

* *2 hours* Thinking about possible rescoping strategies in case the MQTT event loop bug can not be solved in time
* *0.5 hours* Wrote email to supervisor with update on the status of the implementation

## Week 9

### 16 Nov 2021

* *0.5 hours* Prep for next meeting

### 17 Nov 2021

* *0.5 hours* Meeting with supervisor
* *0.5 hours* Aggregated meeting notes

### 19 Nov 2021

* *1 hours* Read into using quiche with tokio and found out that [quiche does not support async](https://github.com/cloudflare/quiche/issues/139) (and is actually built to be called from C) so there are no examples (nor seemingly plans) for it to support tokio
* *1 hours* Read into how tokio uses mio in its implementation and how I could build a tokio wrapper around quiche. Decided to try to switch implementation to quinn because it seems it would be easier to do.
* *2 hours* Wrote initial [re-write of the socket library in quinn](https://github.com/Apolexian/QuicSocket/commit/0cb2040ce8941f13515ad19f16c0bd0f1914f31b)

## Week 10

### 23 Nov 2021

* *2.5 hours* Debugged new implementation in quinn and tried to test it. Can't seem to generate the right certificates that their example would work with. The [example they provide](https://quinn-rs.github.io/quinn/quinn/certificate.html) for generating certificates is also outdated and does not work.
* *2 hours* Read into ssl/tls certificates more and the rustls library to try to figure out why the certificates that I am generating do not work with the [quinn example server](https://github.com/quinn-rs/quinn/blob/main/quinn/examples/server.rs).
* *1 hours* Tried to modify the quinn examples to use pem instead of der but neither work.

### 24 Nov 2021

* *0.5 hours* Meeting with supervisor
* *0.5 hours* Aggregated meeting notes

### 25 Nov 2021

* *1 hours* Debugged the certificate generation further. Decided that I should use rcgen to generate certificates instead of generating them via cli then reading the file. Need to change the code to resemble this.
* *1 hours* Re-wrote the send and recv functions to not use the tls build steps that quinn example uses and instead use code generated certificates and handshake seems to work now. The server does not receive anything so need to debug this. Additionally, this method means that the cert.der is saved on server load to a file and I have to copy and paste it to the client directory for the crypto to work.
* *1 hours* Debugged the server hanging. The payload is received correctly in the handler functions but the `handle_connection` function never returns a value, maybe due to async? It's also rather hard to debug because the client times out if I keep the server debugger going for too long.
* *1 hours* Fixed server hanging issue due to loop behavior. Most of the examples assume the server waits for all connections which is not exactly the case here since I'm trying to use it as a transport for mqtt messages. Had to have a bit of a hacky way to load certificates for the client, when the server loads it generates a certificate for the client and puts it in the path supplied. Could change this later to not generate a new cert every time and just read from a file, but this works for now. I could also need to figure out how to keep the QUIC server running while waiting for more mqtt packets. This would mean that we need to keep the loop going *and* read the thing the client sent, while in all examples we have HTTP so the server simply responds. This can probably be done by having some sort of data structure that we write to and read from to get the current packet, but this would have to be thread-safe.

## Week 11

### 1 Dec 2021

* *0.5 hours* Meeting with supervisor
* *0.5 hours* Aggregated meeting notes

### 2 Dec 2021

* *1 hours* Read into the code for MQTT more to make sure that I'm not getting rid of more than I need to.
* *0.5 hours* Chatted with Paul Traynor about the async issues as he is making a service layer for QUIC for his project and also working in quiche.

### 3 Dec 2021

* *2 hours* Tried to migrate the mqtt client to use the new version of quic socket but encountering some problems with the same eventloop as before. Code might be a bit too complex in rumqtt so will read it more to understand the flow.

### 4 Dec 2021

* *3 hours* Spent time reading the MQTT code and sketching out what I need to change in the socket library.

## Week 12

### 6 Dec 2021

* *1 hours* Went through the examples for quinn again and decided that I need to split my implementation into a client and server structs with respective send and recv methods. Currently recv means that the library thinks you are a server, which is obviously wrong.
* *2 hours* Finished initial implementation of the QUIC server and client for the socket.
* *1 hours* Solved issue with tls certificates not being read from file. It seems that the certificates generated from the CLI were perhaps too short or did not have enough detail? New function in quick socket to generate quinn compliant tls certificates and save them to files. Server and client then read from those files. For now, this is hard coded.
* *0.5 hours* Ported rumqttc and rumqttd to use the new version of quic socket.
* *0.5 hours* Fixed some minor bugs in the mqtt code and realised that I need to pass server address when creating the server already instead of hard coding.

### 7 Dec 2021

* *2 hours* Read more into the rumqtt API and mqtt spec to see what the handling of packets flow is.
* *1 hours* Prep for next meeting.

### 8 Dec 2021

* *0.5 hours* Meeting with supervisor.
* *0.5 hours* Aggregated meeting notes.
* *2.5 hours* Fixing minor bugs in send method of quic implementation.

## Week 13

### 14 Dec 2021

* *1.5 hours* Wrote up the status report.
* *3 hours* Tried to get mqtt implementation working but encountered problem with not knowing how to make broker know where to send a response.
 
 ### 15 Dec 2021

* *0.5 hours* Meeting with supervisor.
* *0.5 hours* Aggregated meeting notes.

### 16 Dec 2021

* *3 hours* More work on mqtt but still encountering both eventloop and other minor issues. May put a pause on this to save some sanity.

### 19 Dec 2021

* *2 hours* Read about way to analyse binary sizes. Found [google's](https://github.com/google/bloaty) that I can use for ngtcp2, since the example server and client are in cpp. [Cargo bloat](https://github.com/RazrFalcon/cargo-bloat) seems to be the equivalent for rust.

## Week 14

### 20 Dec 2021

* *3 hours* Created examples for quiche and quinn in stand-alone cargo binaries in order to be able to analyse them using cargo bloat. Compiled ngtcp2 and used bloaty to analyse that. Also took a look at [mvfst](https://github.com/facebookincubator/mvfst) however this one bundles together client and server, and the binary is unreasonable large compared to ngtcp2. Its hard to find exactly how large the tls component is for quiche because it has its own tls implementation, so on cargo bloat it just shows up as part of the quiche dependency. To get an approximation i've compared how large the source code files are and will create a mock binary that uses all the dependencies that their TLS implementation uses and see how large that is. Same for ngtcp2 that requires some sort of backend to exist, for me this is openssl. I can probably somehow find how large an openssl binary is. For the analysis part of the dissertation I can probably discuss this and just analyse quinn that uses rustls, since this is actually measurable. Also, useful link: <https://en.wikipedia.org/w/index.php?title=Comparison_of_TLS_implementations&oldid=585386367#Code_size_and_dependencies>.

* *3 hours* Went through the dissertation writing guidance on moodle and in the template and adjusted the template sections to be in different files.

### 21 Dec 2021

* *4 hours* Wrote the transport layer background section for the dissertation.
* *3 hours* Wrote up the IoT background section for the dissertation.

### 22 Dec 2021

* *4 hours* Wrote up the rust background section for the dissertation.

### 23 Dec 2021

* *4 hours* Restructured parts of the presentation and skimmed through a few of the hall of fames ones to get an idea of how a more research based project can be structured. 
* *2.5 hours* Started writing the network simulation part of the dissertation (describing how the analysis was done using mininet)

## Week 15

### 28 Dec 2021

* *1 hours* Finished the network simulation section for the dissertation.
* *2 hours* Rethought the way that connection establishment works for quic socket. Stream should be opened in new method.

### 29 Dec 2021

* *1 hours* Re-wrote parts of quic-socket to establish connection and open bidirectional stream in new method. Altered examples to test this.
* *1 hours* Finished new quic-socket implementation and tested it using the quic socket examples. The client and server can now send and receive arbitrary payloads on new streams and there seems to be no hanging and packets arrive fine.
* *3 hours* Debugging invalid packets in mqtt and trying to get it to work. Currently I manage to get the initial connection ACK only, so packets get corrupted somewhere after that.
* *1 hours* Found bug - was reading more bytes than necessary from buffer. MQTT seems to work now with QUIC but using threads makes some messages lost (around 9 out of 100).

## Week 16

### 3 Jan 2022

* *5 hours* Wrote the mqtt background section and started the analysis of QUIC implementations. Got the binary sizes for most of the ones I need but having trouble compiling [msquic](https://github.com/microsoft/msquic).

### 4 Jan 2022

* *1 hours* Wrote the start of the analysis of the quic implementation.
* *1 hours* Had to rethink the dissertation structure because it did not really flow well.
* *2 hours* Got msquic to compile and got the binary size numbers for it, added to the corresponding section.

### 6 Jan 2022

* *3 hours* Edited what I have so far in the dissertation to see if the flow makes sense.
* *1 hours* Wrote the draft for the QuicSocket dissertation section.

## Week 17

### 12 Jan 2022

* *0.5 hours* Meeting with supervisor.
* *0.5 hours* Aggregated meeting notes.

### 14 Jan 2022

* *4 hours* Researched different tools for binary size analysis and read the docs for tcpdump.

## Week 18

### 19 Jan 2022

* *0.5 hours* Meeting with supervisor.
* *0.5 hours* Aggregated meeting notes.

### 20 Jan 2022

* *3 hours* Further reading into bloaty and its rust equivalent. Also read about the freebsd ELF binary analysis tool.

## Week 19

### 24 Jan 2022

* *1.5 hours* Wrote up the analysis plan.

### 25 Jan 2022

* *2 hours* Meeting prep and going over analysis plan.

### 26 Jan 2022

* *0.5 hours* Meeting with supervisor.
* *0.5 hours* Aggregated meeting notes.

## Week 20

### 31 Jan 2022

* *3 hours* Read into examples of smart factories using IoT to come up with a representative topology. In the end decided to settle for a 3d printer farm as its something I have a little bit of experience in.
* *1 hours* Read into MQTT use in 3d printer farms, but didnt find any papers, just blogs with not so useful info.

### 1 Feb 2022

* *1 hours* Created an example topic and messages that will be used for the mqtt testing.
* *1 hours* Extracted the base mqtt script needed to run mqtt for both client and broker.
* *1 hours* More trying to get tcpdump to work within mininet.
* *2 hours* Debugged mininet topology making hosts unreachable, it seems that mininet can not handle circular topologies well.

### 2 Feb 2022

* *2 hours* Recorded data for the base rumqtt TCP implementation using tcpdump and created a filtering script for the dump data.
* *0.5 hours* Meeting with supervisor.
* *0.5 hours* Aggregated meeting notes.
  
### 3 Feb 2022

* *1.5 hours* Re-wrote parts of the network sim chapter in the dissertation to reflect new scenarios and topology.

### 5 Feb 2022

* *6 hours* Wrote up remaining sections of the diss to see how it will flow, leaving results and conclusion blank.

### 6 Feb 2022

* *2 hours* Debugged hostnames not working in mininet. Currently trying to use the hostnames supplied by mininet, but these are likely not DNS resolvable.
