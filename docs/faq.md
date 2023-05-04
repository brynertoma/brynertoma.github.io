# FAQ 🐉

## Who is this for?
`AES` is here to make your code modular so that you can design your systems in a way where they don't depend on each other. It is for anyone who is serious about designing a game and ensuring their code or blueprints are reusable, decoupled and free from a ton of dependencies.

This gives you the freedom of reusing `System A` without ripping the whole project apart to bring in `System B`, `System C` and `System X/Y/Z` and a bunch of other unrelated content systems just because `System A` had a hard reference to an object that belongs to another system.

`AES` is for developers that don't want to keep track of all sorts of variables and do a bunch of casting to see if it's the inventory component that's talking to the crafting component which might be talking to the building component that might be talking to the game mode, game state or some other player controller, pawn or whatever.

Simply create an `Identity` for any actor, component, or object and now your object has the freedom to talk to any other system within your game without knowing anything about that system.

Don't be a noob! Decouple your code and make some real spaghetti 🍝, not code spaghetti 👩‍💻.

## What do I need to know?
Basic Blueprint experience and navigation of Unreal is all that is required. If you're working on a multiplayer game, you may need to understand the `Server` - `Client` architecture of Unreal as well as the basics of `Remote Procedure Calls` or `RPCs`.

## Is this replicated?
**Purposfully no**. 

In order to keep the `Event Manager` as efficient as possible, we've separated `Server` events from `Client` events. This removes a lot of overhead and uncessary iteration for events that are run on the `Client` just for *visual* or *cosmetic* effects.

This also removes the overhead that comes with Unreal's replication system by avoiding the "polling" method that Unreal uses for replicated properties.

If you have a gameplay event that needs to be authoritive but you want `Clients` to hear it, simply register for that event on the **server side only** and when that event occurs, call a `Multicast RPC` passing in **only the data that the client needs** to replicate that event within their own game instance.

The focus of `AES` is to make your game **as event-based as possible**, which means we want to avoid "polling" at all costs since it is the antithesis of event-based programming. This is why we've chosen to leave replication of events up to the end user with the very strong recommendation of using `RPCs` to do so.

## How do I enable the plugin?
Once you've **[purchased the plugin](https://www.unrealengine.com/marketplace/en-US/product/AES)** you can simply click `Install to Engine` and then launch your project and go to `Edit` -> `Plugins` -> `Awesome Systems` -> `AES` and enable it. 

You'll be prompted to restart your editor and once that's complete, you'll have access to all of the custom nodes that `AES` provides!

## Is this compatible with UE4? What about UE5?
Yes and yes. AES is designed on UE5 Main which is typically 1-2 versions ahead of UE5 Release. This allows us to ensure that as soon as Epic releases a new Engine version, we can update our plugin with a click of a button and be confident that it will continue to work should you decide to upgrade your project to the latest Unreal Engine version.