# COMPUTER_NETWORKING
This repo has all files that contains some of Computer Networking applications such as:
  1. Two TCP/IP Chat Clients Connected through a TCP Chat Server
  2. File Transfer from Client to Server using TCP
  3. Simulation of Sliding Window Protocol with Selective Repeat
  4. CSMA Network Performance Measurement with NS3 Simulator

A brief information about each of these are mentioned below:
  1. Two TCP/IP Chat Clients Connected through a TCP Chat Server.
  Summary: The Chat Server will be running on a host. The same chat client applications will be run on two different     hosts. In this assignment, you have to write a TCP Client and TCP Server applications in C programming language.     Both the applications should run on Ubuntu host (above 16.04+ version).
  
 After both client applications are up, Client-1 should display a chat prompt as:

Connected to Client-2:> hello user 2, how are you?

Client-2:: I am fine, user-1!

Connected to Client-2:>

Connection to Client-1 is closed.

-----

Client-2 should display a chat prompt as:

Connected to Client-1:> 

Client-1:: hello user 2, how are you?

Connected to Client-1:> I am fine, user-1!

Connected to Client-1:>  ....

Connected to Client-1:> quit   OR exit

  2. File Transfer from Client to Server using TCP
  Summary: In this assignment, you have to write a TCP Client and TCP Server applications in C programming language.      Both the applications should run on Ubuntu host (above 16.04+ version).
     The client should transfer a file located in its local file system to the server. The server should save the        received file in a directory named: received_files in its current working directory.

The sending of a file at the client is initiated by the command:

$ transfer-client -s 192.168.1.10

Connected to the server at IP Address: 192.168.1.10

> send <file-1>

File-1 has been sent to the server successfully
>
  
The client and server should follow the following protocol:

  
Client                                                  Server
  
  ----------  SENDING <File-1> 1275 bytes ---------->
  
  <--------- RECEIVE-READY <File-1> 1275 bytes ------
  
  ---------- Contents of the <File-1>--------------->
  
  ---------- Contents of the <File-1>--------------->
  
  ---------- Contents of the <File-1>--------------->
  
  <--------- RECEIVED <File-1> 1275 bytes ------------

  
  3. Simulation of Sliding Window Protocol with Selective Repeat
  Summary: In this assignment, you have to write a Sender and Receiver TCP socket applications in C programming         language. Both the applications should run on Ubuntu host (above 16.04+ version).The Sender and Receiver should simulate the Sliding Window Protocol with Selective Repeat.The activity of sending and receiving the packets should be logged (printed) to the console in which the application is started. The sender application will connect to the receiver application by executing the following command:

$ sender_app -c 192.168.1.10

Connected to the receiver at IP Address: 192.168.1.10

The Sender and Receiver should follow the protocol as specified below:

Sender                                         Receiver

        ----------  Sent Packet-1 ---------->

        ----------  Sent Packet-2 ---------->

        ----------  Sent Packet-3 ---------->

        ----------  Sent Packet-4 ---------->

        ----------  Sent Packet-5 ---------->

        ----------  Sent Packet-6 ---------->

        ----------  Sent Packet-7 ---------->

        ----------  Sent Packet-8 ---------->

        ----------  Sent Packet-9 ---------->

        ----------  Sent Packet-10 --------->

        <---------  Sent NACK Packet-4 -----

        ----------  Resent Packet-4 -------->

        <---------  Sent NACK Packet-7 -----

        ----------  Resent Packet-7 -------->

The Window sizes on the Sender and Receiver accept the sizes as input from the console. For example, if the Receiver's window size is 5, a random number should be generated between 1 to 5 and packet with that index in the window has to be considered that it has error (lost or data errors).

The sender can send max 5 packets per second. The sender should sent next batch of packet (next group of 10 packets in the following example) only after ensuring that all packets sent in the current batch are received by the receiver.

In the simulation run, the sender should send 50 packets and all of them should be received by the Receiver.

The log messages displayed in the console windows of Sender and Receiver are as follows:

Sender                                   Receiver                    
          
Generate a random number: 1 to 5

Enter Window Size: 10      Enter Window Size: 5

Sent Packet-1                       Received Packet-1

Sent Packet-2                       Received Packet-2

Sent Packet-3                       Received Packet-3

Sent Packet-4                       Error in Packet-4       Random number generated: 4

Sent Packet-5                       Received Packet-5

Sent Packet-6 

Sent Packet-7 

Sent Packet-8 

Sent Packet-9 

Sent Packet-10 

              <-----------------    Sent NACK for Packet-4

Received NACK for Packet-4

Resending Packet-4                  Received Packet-4  

                                                                                               Random number generated: 2

                                    Received Packet-6 

                                    Error in Packet-7                                

                                    Received Packet-8                                     

                                    Received Packet-9 

                                    Received Packet-10                                    

        <-----------------   Sent NACK for Packet-7   (5 + 2 = 7)

Received NACK for Packet-7               

Resending Packet-7         

                     . . . .

                     . . . .

                     . . . .

Sent Packet-49                      Received Packet-49    

Sent Packet-50                      Received Packet-50    

  4. CSMA Network Performance Measurement with NS3 Simulator
  Summary: In CSMA/CD, the size of a frame must be large enough so that collision can be detected by sender while       sending the frame. So, the frame transmission delay must be at least two times the maximum propagation delay. 
   
    Assume some station transmitted data packet and successfully get to the destination but it just the Best Case, so we have to take Worst Case scenario in which there will be contention slots. Contention slots are those slot which are not able to transmit their journey due to the collision. Suppose A station transmitted data but collide and worst case time wasted is 2Tp and then some station B found out a way to transmit the data so it took.

Efficiency = Tt / ( C*2*Tp + Tt + Tp) 

Tt : transmission time

Tp: propagation time

C: number of collision

Put a = Tt/Tp

Efficiency = 1/ (1 + 6.44a)

            = 1/ {1 + 6.44(Tp/Tt)}

            = 1/ {1 + 6.44((distance/speed)(Bandwidth/packet length))}

   802.3 Carrier Sense Multiple Access/Collision Detection (CSMA/CD) segment is measured resulting in throughput, response times and workstation parameters for several network nodes. During the measurements, the network carried an artificial workload with the characteristics of a real-life workload.

   Develop NS3 simulation using the artificial workload parameters and the 802.3 CSMA/CD standard. The measurements show that it is possible to determine the workstation parameters with great accuracy using simple throughput measurements on an otherwise empty network.  It is then possible to isolate exact Ethernet parameters during throughput measurements on a network with a known workload. 

   The behavior measured is reproduced in a simple simulation. The results of the simulation conform to the measured values.  Parameters that can be used to fine-tune the simulation are the inter-frame gap time and the workstation distance on a network.
