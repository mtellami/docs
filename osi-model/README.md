<div align="center">

# 🪩 OSI model 🪩
</div>

OSI stands for Open Systems Interconnection. The OSI model, created in 1984 by ISO, is a reference framework that explains the process of transmitting data between computers. It is divided into seven layers that work together to carry out specialised network functions, allowing for a more systematic approach to networking.
<img src="src/osi-layers" width="100%" />

## 🔷 Physical Layer
The lowest layer of the OSI Model is concerned with electrically or optically transmitting raw unstructured data bits across the network from the physical layer of the sending device to the physical layer of the receiving device. It can include specifications such as voltages, pin layout, cabling, and radio frequencies. At the physical layer, one might find “physical” resources such as network hubs, cabling, repeaters, network adapters or modems.

### 🔸 Functions of the Physical Layer
- Bit synchronization: The physical layer provides the synchronization of the bits by providing a clock. This clock controls both sender and receiver thus providing synchronization at the bit level.
- Bit rate control: The Physical layer also defines the transmission rate i.e. the number of bits sent per second.
- Physical topologies: Physical layer specifies how the different, devices/nodes are arranged in a network i.e. bus, star, or mesh topology.

## 🔷 Data Link Layer
The data link layer is responsible for the node-to-node delivery of the message. The main function of this layer is to make sure data transfer is error-free from one node to another, over the physical layer. When a packet arrives in a network, it is the responsibility of the DLL to transmit it to the Host using its MAC address.<br/> 
The Data Link Layer is divided into two sublayers:  

### 🔹 Logical Link Control (LLC)
Logical Link Control (LLC) is a sublayer that generally provides the logic for the data link as it controls the synchronization, multiplexing, flow control, and even error-checking functions of DLL (Data Link Layer). 

### 🔹 Media Access Control (MAC)
MAC Addresses are unique 48-bit hardware numbers of a computer that are embedded into a network card (known as a Network Interface Card) during manufacturing. The MAC Address is also known as the Physical Address of a network device.

The packet received from the Network layer is further divided into frames depending on the frame size of the NIC(Network Interface Card). DLL also encapsulates Sender and Receiver’s MAC address in the header.<br/> 
The Receiver’s MAC address is obtained by placing an ARP(Address Resolution Protocol) request onto the wire asking “Who has that IP address?” and the destination host will reply with its MAC address.  

### 🔸 Functions of the Data Link Layer
- Framing: Framing is a function of the data link layer. It provides a way for a sender to transmit a set of bits that are meaningful to the receiver. This can be accomplished by attaching special bit patterns to the beginning and end of the frame.
- Physical addressing: After creating frames, the Data link layer adds physical addresses (MAC addresses) of the sender and/or receiver in the header of each frame.
- Flow Control: The data rate must be constant on both sides else the data may get corrupted thus, flow control coordinates the amount of data that can be sent before receiving an acknowledgment.

## 🔷 Network Layer
The network layer works for the transmission of data from one host to the other located in different networks. It also takes care of packet routing i.e. selection of the shortest path to transmit the packet, from the number of routes available. The sender & receiver’s IP addresses are placed in the header by the network layer. 

### 🔸 Functions of the Network Layer
- Routing: The network layer protocols determine which route is suitable from source to destination. This function of the network layer is known as routing.
- Logical Addressing: To identify each device on Internetwork uniquely, the network layer defines an addressing scheme. The sender & receiver’s IP addresses are placed in the header by the network layer. Such an address distinguishes each device uniquely and universally.

## 🔷 Transport Layer
The transport layer provides services to the application layer and takes services from the network layer. The data in the transport layer is referred to as Segments. It is responsible for the End to End Delivery of the complete message. The transport layer also provides the acknowledgment of the successful data transmission and re-transmits the data if an error is found.

- At the sender’s side: The transport layer receives the formatted data from the upper layers, performs Segmentation, and also implements Flow & Error control to ensure proper data transmission. It also adds Source and Destination port numbers in its header and forwards the segmented data to the Network Layer.<br/> 
- At the receiver’s side: Transport Layer reads the port number from its header and forwards the Data which it has received to the respective application. It also performs sequencing and reassembling of the segmented data. 

### 🔸 Functions of the Transport Layer
- Segmentation and Reassembly: This layer accepts the message from the (session) layer, and breaks the message into smaller units. Each of the segments produced has a header associated with it. The transport layer at the destination station reassembles the message.
- Service Point Addressing: To deliver the message to the correct process, the transport layer header includes a type of address called service point address or port address. Thus by specifying this address, the transport layer makes sure that the message is delivered to the correct process.

## 🔷 Session Layer
This layer is responsible for the establishment of connection, maintenance of sessions, and authentication, and also ensures security.

### 🔸 Functions of the Session Layer
- Session establishment, maintenance, and termination: The layer allows the two processes to establish, use and terminate a connection.
- Synchronization: This layer allows a process to add checkpoints that are considered synchronization points in the data. These synchronization points help to identify the error so that the data is re-synchronized properly, and ends of the messages are not cut prematurely and data loss is avoided.

## 🔷 Presentation Layer
The presentation layer is also called the Translation layer. The data from the application layer is extracted here and manipulated as per the required format to transmit over the network. 

### 🔸 Functions of the Presentation Layer
- Translation: For example, ASCII to EBCDIC.
- Encryption/ Decryption: Data encryption translates the data into another form or code. The encrypted data is known as the ciphertext and the decrypted data is known as plain text. A key value is used for encrypting as well as decrypting data.
- Compression: Reduces the number of bits that need to be transmitted on the network.

## 🔷 Application Layer
At the very top of the OSI Reference Model stack of layers, we find the Application layer which is implemented by the network applications. These applications produce the data, which has to be transferred over the network. This layer also serves as a window for the application services to access the network and for displaying the received information to the user. 

### 🔸 Functions of the Application Layer
- Network Virtual Terminal: It allows a user to log on to a remote host.
- FTAM- File transfer access and management : This application allows a user to access file in a remote host, retrieve files in remote host and manage or control files from a remote computer.

## conclusion

|        Layer       |                                  Responsibility                               | Data unit |      Device of Protocol      |
|:------------------:|:-----------------------------------------------------------------------------:|:---------:|:----------------------------:|
| Application Layer  | Helps in identifying the client and synchronizing communication.              |  Message  | SMTP                         |
| Presentation Layer | Extracte and manipulate data in the required format for transmission.         |  Message  | JPEG, MPEG, GIF              |
| Session Layer      | Establishes Connection, Maintenance, Ensures Authentication and security.     |  Message  | Gateway                      |
| Transport Layer    | Take Service from Network Layer and provide it to the Application Layer.      |  Segment  | Firewall                     |
| Network Layer      | Transmission of data from one host to another, located in different networks. |  Packet   | Router                       |
| Data Link Layer    | Node to Node Delivery of Message.                                             |  Frame    | Switch, Bridge               |
| Physical Layer     | Establishing Physical Connections between Devices.                            |  Bits     | Hub, Repeater, Modem, Cables |

.
