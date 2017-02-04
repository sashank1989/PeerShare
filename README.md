# PeerShare
A Simple Napster Style P2P File Sharing System

PeerShare has two components:
	
	1. A central indexing server
		This server indexes the contents of all of the peers that register with it. 
		It also provides search facility to peers. In our simple version, we have not
		implemented sophisticated searching algorithms; but an exact match.
		
		The server provides the interface similar to ones mentioned below to the peer clients:
			registry(peer id, file name, ...) 
				Invoked by a peer to register all its files with the
				indexing server. The server then builds the index for the peer. 

			lookup(file name)
				This procedure should search the index and return all the matching peers to the requestor.
	
	2. A peer
		A peer is both a client and a server. 
		As a client, the user specifies a file name with the indexing server using "lookup". 
		The indexing server returns a list of all other peers that hold the file. 
		The user can pick one such peer and the client then connects to this peer and downloads the file. 
		As a server, the peer waits for requests from other peers and sends the requested file when receiving a request.

		The peer server provides the interface similar to one mentioned below to the peer client:
 			retrieve(file name)
				Invoked by a peer to download a file from another peer. 

			
			
Other Features:
	1. Both the indexing server and a peer server are able to accept multiple client requests at the same time.
	2. Each peer has an automatic update mechanism. 
			If a user modifies or deletes some files registered at a server, 
			the effect is reflected to the server in time. 
			For example, if a user deletes a file on the disk, the server is notified in time 
			and server removes the corresponding item from the index server.
			

Source privately hosted at https://bitbucket.org/sashankbv/peershare