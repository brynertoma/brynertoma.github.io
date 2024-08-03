![image](../../img/AESManager.png)

?> **NOTE**: You will never need to use this node since the custom AES nodes will be talking to the `AES Manager` behind the scenes. This is just for educational purposes only. 

The `AES Manager` is a `World Subsystem` that is created on the `Server` and the `Client`.

It's job is to initalize all `AES Event` classes (Blueprint and C++) in the project and preallocate memory for the arrays used to store the delegates for each type of event. This happens on intialization as soon as the `Asset Manager` has completed its initial asset scan.

The `AES Manager` is also responsible for maintaining a list of registered `Identities` as well as tracking which `Identities` are listening to what events. The `AES Statics` class is a `Blueprint Function Library` that calls the `Register/Unregister for X Event` methods on the `AES Manager` as well as the `Generate Event` method.

?> **NOTE**: The `AES Manager` has some internal static methods as well (`CreateEventInternal`, `GenerateEventInternal` and `CreateAndGenerateEvent`) to allow users to generate events from C++ without having to call the Blueprint-exposed methods that have additional overhead due to the UFUNCTION() macro.
