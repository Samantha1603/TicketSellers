TicketSellers
=============
	We writing a multithreaded program using C++ and the Pthreads library. Write a program that simulates ticket sellers simultaneously selling concert tickets during one hour.

Suppose there are 100 seats available to a concert. One ticket seller named H sells high-priced tickets, three ticket sellers named M1, M2, and M3 sell medium-priced tickets, and six ticket sellers named L1, L2, L3, L4, L5, and L6 sell low-priced tickets. Each ticker seller has a separate customer queue. 

All the ticket sellers work simultaneously during one hour. Each seller can expect N customers to arrive at random times during the hour, where N is a command-line parameter. Each seller serves customer in the order that they arrive in his ticket queue.



Multi-threaded Ticket Sellers Report
	
	To match the feel of a ticket vendor, we opened up 10 threads that handle the different seller prices. Each customer has another individual thread, which we put into queues. There are 10 queues total, each corresponding to a different seller thread. There is also a timer thread that keeps track of time for all sellers. Meanwhile, the program can handle impatient customers so they will leave the queue after 10sec and remove from the queue. 
	
	To make sense for realism, we needed to make sure the sellers were behaving correctly in all of its cases, in which there are customers, or when their line is empty. Customers also are kept on their own thread to represent single people, instead of having a group of people in one thread. The shared and critical regions are the queues and seat that each seller thread maintains during adding customers to the queue, removing customers from the queue and assigning seats to the seat array.  When a customer wants to get in line, they get in one process at a time, to keep the queue from getting disorganized. The only synchronization needed was the timing for all the sellers. For that we had a timer thread keep track for how long a minute would last.
