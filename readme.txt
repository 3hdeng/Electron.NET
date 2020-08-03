//=== 2020.08.03
$ Electron.NET/
$ cd ElectronNET.CLI


Electron.NET/ElectronNET.CLI/
$ dotnet build


[Q] how to install local nuget package ?
https://docs.microsoft.com/en-us/nuget/consume-packages/install-use-packages-nuget-cli

-->
$ dotnet tool install ElectronNET.CLI -g
You can invoke the tool using the following command: electronize
Tool 'electronnet.cli' (version '99.0.0') was successfully installed.


-->
$ dotnet tool install ElectronNET.CLI -g
Tool 'electronnet.cli' is "already" installed.

$dotnet tool uninstall ElectronNET.CLI -g
Tool 'electronnet.cli' (version '99.0.0') was successfully "uninstalled".

$ dotnet tool install ElectronNET.CLI -g
You can invoke the tool using the following command: electronize
Tool 'electronnet.cli' (version '99.0.0') was successfully installed.


//===
$ cd $dir/ElectronNET.API
//dotnet restore
$ dotnet build
 Successfully created package 'Electron.NET/artifacts/ElectronNET.API.99.0.0.nupkg'.

$  dotnet tool install ElectronNET.API -g
-->
[error NU1212]: Invalid project-package combination for ElectronNET.API 99.0.0. DotnetToolReference project style can only contain references of the DotnetTool type

Tool 'electronnet.api' failed to install. This failure may have been caused by:
...
* A package by this name was found, but it was not a .NET Core tool.
...

-->  include project reference to ElectronNET.API
$ dotnet add reference ../ElectronNET.API(API proj location)
  or  
$ dotnet add package ElectronNET.API
package location(artifacts) is hidden in NuGet.config

has to cp NuGet.config to another proj which needs ElectronNET.API




//=== 2020.07.27
[Q] diff between electronize start and F5 debug ?
F5 debug --> pure asp.net core app ? no connection with electronjs yet ??



$ electronize build /target linux
... a few mins

$ electronize start

found 1 low severity vulnerability
  run `npm audit fix` to fix them, or `npm audit` for details
../../ElectronHostHook/connector.ts(2,33): 
error TS2503: Cannot find namespace 'SocketIO'.

../../ElectronHostHook/excelCreator.ts(1,24): 
error TS2307: Cannot find module 'exceljs' or its corresponding type declarations.

../../ElectronHostHook/excelCreator.ts(2,37): 
error TS2307: Cannot find module 'exceljs' or its corresponding type declarations.

../../ElectronHostHook/index.ts(7,25): 
error TS2503: Cannot find namespace 'SocketIO'.

Invoke electron - in dir: /home/elf/workspaces/Electron.NET/ElectronNET.WebApp/obj/Host/node_modules/.bin
ATTENTION: default value of option force_s3tc_enable overridden by environment.
Electron Socket IO Port: 8000
Electron Socket started on port 8000 at 127.0.0.1
ASP.NET Core Port: 8001
stdout: Use Electron Port: 8000
stdout: ASP.NET Core host has fully started.




//=== 2020.07.24
ElectronNET.CLI : commandline client invoke electronjs [electron main.js];
not to convert cs to js , it rather wrap electronjs and dotnetApp
-->  electronize ?

ElectronNET.WebApp : web client app in cs
ElectronNET.Host : electronjs http server (js)

ElectronNET.API is like a proxy in C# for electonjs api ???
--> electrojs api
https://www.electronjs.org/docs/api


--> ElectronNET.API proxy API methods  via BridgeConnector.Socket.Emit()
 

//=== ElectronNET.Host : electronjs http server

electronjs http server , http://localhost:port
121 server = require('http').createServer();
122 io = require('socket.io')();
123 io.attach(server);
125 server.listen(port, 'localhost');


???
`/electronPort=${electronPort}`, `/electronWebPort=${aspCoreBackendPort}`

electronPort : ?
electronWebPort: backend http server listening port





//===
