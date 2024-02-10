Here is a detailed documentation on how to run and test the distributed system

1.	Setup
Check to ensure that your system has python IDE installed and if not install
The distributed system code can be downloaded or cloned from the specified repository.
2.	Running the System
Open command prompt and search for the directory that has the distributed system code. Write the following command in command prompt to run the coordinator script.
   “Python coordinator.py”
This command starts the coordinator which is responsible for checking on the status of the server as well as redistributing clients.
3.	Starting Servers
Open a new window tab and start the server instance by running the command below for each server port-8080,8081,8082
“Python server.py <port number>”
Replace port number with the port number of your choice.    
4.	Client Registration
Execute the command below in a new window to test for client registration. The command will connect a client to one of the available servers and return “Registration successful!” if the registration process is successful     
5.	Data Sharing
Upon registration of the client, test the data sharing by sending messages to different clients
Execute more client instances by running the client.py script and observe the broadcasted data received by other clients
6.	Fault Tolerance
Testing for fault tolerance requires one to simulate server failures by manually stopping more server instances. Check to ensure that the coordinator is able to detect the unresponsive servers and redistribute clients to operational servers. Confirm that client registration and data sharing continue even in the event of server failures.
     7.  Testing
   Create and run test cases covering a range of scenarios, such as normal operation, server failures, and data sharing, in order to carry out thorough testing.
  To systematically run through test cases and confirm the desired results, use automated test scripts.
  Record the test results, covering the entire test coverage, any problems that arose, and their fixes.
7.	Debugging and Maintenance
Debugging the code will help you find and fix the core causes of any problems that occur during testing.
   Make the required changes to the codebase in light of the feedback and observations from testing.
   Tests should be run again to make sure that any issues are fixed.

Implemented Feature Documentation
1. Server Setup
There are several server instances created, each listening on a separate port. For every server instance, the `start server` function initializes a TCP socket, binds it to the designated port, and waits for client connections. Every client is handled by a different thread that is created upon connection.
2. Client Registration
By creating a TCP connection to the server address and port, clients can register with a particular server instance using the `register client` function. It sends a request for registration and wait for the server's response. It prints a success message in the event that the registration is successful (shown by a "SUCCESS" response); if not, it prints a failure message.
3. Data Sharing
Data sharing between linked clients is made possible through client-server interaction. When a client sends data to the server, the server broadcasts that data to every other client that is connected, allowing clients to share data.
4. Fault Tolerance
 The system uses a heartbeat mechanism to handle server failures. Every server instance communicates with a central coordinator via heartbeat messages on a regular basis. The coordinator redistributes clients to other servers that are up and running if it does not hear back from a server within a predetermined timeout period. The functions `check_server_statuses}, `handle_heartbeat`, and `redistribute_clients` are accountable for tracking server statuses, identifying malfunctions, and reassigning clients, in that order.

Screenshot of the code execution

 ![Screenshot (386)](https://github.com/Odhiambo2001/readme/assets/107328895/f429a5ba-f551-4591-938a-a377e869c018)

Testing the Distributed System in the event of server failure  and data sharing
1. Server Failure Event:
     1. Start the distributed system with multiple server instances running.
     2. Simulate a server failure by terminating one of the server processes.
     3. Observe how the system responds to the server failure and redistributes clients to operational servers.
   Steps
1. Run the Python script to begin the distributed system.
2. Monitor the support output to guarantee that all servers and the coordinator are started effectively.
3. Simulate a server failure by ending one of the server processes using the appropriate system commands or manual intervention.
4. Observe the console output to see how the system identifies the server failure.
5. Verify that the facilitator redistributes clients to operational servers.
6. Check the connectivity of clients and guarantee that they can proceed with interacting with the system seamlessly despite the server failure.
   Expected Results
   The framework ought to nimbly handle the server disappointment without smashing or causing disturbances to the associated clients.
Clients ought to be effectively redistributed to other operational servers, keeping up continuous communication and information sharing capabilities.
 2. Data Sharing Event  
     1. Start the distributed system with multiple server instances running.
     2. Connect multiple clients to different server instances.
     3. Share data among the connected clients through the servers.
     4. Verify that the shared data is successfully broadcasted to all connected clients.
   Steps
     1. Run the Python script to start the distributed system.
     2. Connect multiple clients to different server instances using the appropriate client registration function (`register_client`).
     3. Send data from one client to another through the server.
     4. Monitor the console output to ensure that the shared data is received and broadcasted to all connected clients.
     5. Test various scenarios of data sharing, including sending different types of data (e.g., text, files) and testing concurrency with multiple clients sharing data simultaneously.
   Expected Results
    Data sent by one client should be successfully received and broadcasted to all other connected clients.
    The system should handle concurrent data sharing among multiple clients without data loss or interference.
   Clients should receive the shared data promptly and consistently, demonstrating robust data sharing functionality.

