Multi-Threaded Proxy Server in C
This project delivers a multi-threaded proxy server, built entirely in C. It draws inspiration for its HTTP parsing from the foundational work found in this Proxy Server repository.
Project Insights
Introduction to the Proxy Server
This proxy server acts as an intermediary between your browser and the internet. When you make a request, it first goes to the proxy, which then forwards it to the destination server. The response from the server returns to the proxy, and only then is it sent back to your browser. This architecture allows for various powerful features.
How Our Proxy Handles Requests
The core functionality of our proxy server involves managing and processing web requests. Here's a simplified view of its operational flow:
Leveraging Multi-threading for Concurrency
To efficiently handle multiple client requests simultaneously, we've implemented multi-threading. Our approach specifically utilizes semaphores for thread synchronization, a more streamlined choice compared to condition variables or pthread_join().
While pthread_join() requires a specific thread ID to wait for, semaphores (with sem_wait() and sem_post()) offer a simpler, parameter-free mechanism for managing thread access to shared resources, making them an excellent fit for this project.
Why Build a Proxy Server?
This project was developed to provide a deeper understanding of several key networking and concurrency concepts:
 * Request Flow: Grasping how web requests travel from a local machine to a remote server.
 * Concurrent Handling: Learning to manage and respond to numerous client requests at once.
 * Concurrency Control: Implementing locking procedures to ensure data integrity in multi-threaded environments.
 * Caching Mechanisms: Exploring the concept of web caches and their role in improving performance.
Beyond learning, proxy servers offer practical benefits:
 * Performance Enhancement: They can significantly speed up Browse and reduce server load through caching.
 * Content Filtering: Proxies can restrict access to specific websites, useful for network administrators.
 * Anonymity: A well-configured proxy can mask the client's original IP address, enhancing privacy.
 * Security: Proxies can be modified to encrypt requests, adding a layer of security against eavesdropping.
Key OS Components Utilized
Our proxy server makes extensive use of the following operating system components:
 * Threading: For handling concurrent client requests.
 * Locks: To protect shared data structures from race conditions.
 * Semaphores: For robust thread synchronization.
 * Cache: Implemented with an LRU (Least Recently Used) algorithm to store and retrieve web content efficiently.
Current Limitations
While powerful, this project currently has a few limitations:
 * Complex URLs and Caching: If a single URL triggers multiple internal client requests (e.g., for different resources), our cache might store each response as a separate entry. This can lead to incomplete page rendering if only a portion of the cached content is retrieved.
 * Fixed Cache Element Size: The cache elements have a fixed size, meaning very large web pages or resources might not be fully stored.
Future Enhancements
This project offers several avenues for further development:
 * Multiprocessing Implementation: Shifting to a multiprocessing model could offer true parallelism and potentially higher performance.
 * Advanced Content Filtering: Expanding the code to allow for more sophisticated website whitelisting or blacklisting rules.
 * POST Request Support: Adding support for HTTP POST requests to handle form submissions and other data-sending operations.
Getting Started
Ready to run your own proxy server? Follow these simple steps:
 * Clone the repository:
   git clone https://github.com/Dhruvkoshta/Web-Server-in-C.git

 * Navigate into the directory:
   cd Web-Server-in-C.

 * Build the project:
   make all

 * Run the proxy server:
   ./proxy <port no.>

   Replace <port no.> with your desired port (e.g., ./proxy 8080).
Once the server is running, you can access websites through it by configuring your browser or by using a URL format like this:
http://localhost:port/https://www.cs.princeton.edu/
Important Notes
 * This proxy server is designed to run specifically on Linux machines.
 * Disable your browser's cache when testing to ensure you're seeing the proxy's caching behavior.
 * To run the proxy without the cache, you'll need to adjust the Makefile to compile proxy_server_without_cache.c instead of proxy_server_with_cache.c. Simply change the filename reference in the Makefile.
Demo
Observe the caching in action:
 * When you first access a website through the proxy, you'll see a url not found message, indicating a cache miss.
 * Subsequent visits to the same website will print Data is retrieved from the cache, confirming the content was served from the proxy's cache.

