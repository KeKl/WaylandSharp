Wayland C# Binding
===================


This repo contains the source code of Wayland C# bindings!

----------


Build status
-------------

No build server available.

----------


Basic example
-------------------

#### Open a connection to the default display

```
// Open conection
var display = Display.Connect();

if(display == null)
	throw new NotSupportedException("Can't connect to display.");

```

#### Get the global registry of the display

```
// Get registry
var registry = display.GetRegistry();

if(registry == null)
	throw new NotSupportedException("Registry can´t be null.");

```

#### Add the listener to the registry

```
// Add listener
registry.AddListener(GlobalRegistryHandler, GlobalRegistryRemover, IntPtr.Zero);
```

Definition of the generic handler:
```
private void GlobalRegistryHandler(
			IntPtr data, 
			ref IntPtr wlRegistry, 
			int id, 
			string interfaceName,
			int version)
{
	Debug.WriteLine(
		String.Format(
			"Got a registry event for {0} with {1}.", 
			interfaceName,
			id
		)
	);
}
		
private void GlobalRegistryRemover(
			IntPtr data, ref IntPtr wlRegistry, int id)
{
	Debug.WriteLine(
		String.Format(
			"Got a registry losing event for {0}.",
			id
		)
	);
}
```
