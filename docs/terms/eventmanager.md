![image](../../img/AESManager.png)

?> **NOTE**: You will never need to use this node since the custom AES nodes will be talking to the `AES Manager` behind the scenes. This is just for educational purposes only. 

The `AES Event Manager` is a `World Subsystem` that is created on the `Server` and the `Client`.

It's duty is to initalize all `AES Event` assets in the project and build the appropriate lists required to make the system work. This happens on intialization as soon as the `Asset Manager` has completed its initial asset scan.

These lists are sorted parallel arrays that are managed by the `AES Event Manager` and are updated any time an `Identity` registers or
unregisters from various events.

By using parallel sorted arrays, we have a great benefit of being able to run binary searches to find the index of the event we need much faster than regular arrays.

Also since arrays are stored sequentially in memory, this makes our data extremely cache friendly compared to other data types like Maps.

As a ridiculous example, if you have `INT64` size of events in a single list (9,223,372,036,854,775,807 events), our **max** number of iterations to find any event is 64 iterations. 

?> **NOTE** Please note that this is a very unrealistic scenario but it was purely to demonstrate the power of binary searches. This also assumes your data set is of a decent size since a regular search from start to end may perform better in cases where your lists are small. \nAn event system is more than likely going to be keeping track of a good amount of events and internal testing with actual gameplay concluded that sorted binary searches performed the best compared to other methods.
