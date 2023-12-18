# blazor-typings
Prototype TypeScript typings for Blazor Web | proto `@types/blazor`

This project was made public to allow people to use the `Blazor` JavaScript variable from TypeScript (or JavaScript) with type information.

With .NET 8, the public API surface of the global `Blazor` JavaScript object used to interact with Blazor got larger. However, as the `blazor.*.js` files are being distributed via the SDK (in related NuGet packages) and not via *npm*, it is a bit wonky to use this API. Seeing as the source was already in TypeScript, it was pretty straightforward to create the type definitions (`.d.ts`) for the API. However, the API is only annotated where there were comments already available from the official [dotnet/aspnetcore repo](https://github.com/dotnet/aspnetcore/tree/889b89f6000b60ac6310c152f799e90a3f1ee245/src/Components/Web.JS). More info: [`Blazor` JavaScript object and related type definitions should be available (`@types/blazor`, `@types/dotnet`) aspnetcore#52629](https://github.com/dotnet/aspnetcore/issues/52629).

This project was made for those who want a simple but working solution for the typed Blazor JavaScript API until an official solution is published by the .NET teams, possibly in .NET 9.

The APIs included in this type definition only cover the new unified Blazor Web (WebAssembly + Server + SSR) model, and not the previously available Blazor WebAssembly and Blazor Server models.

If someone would like to take this repository as a starting point to publish a package to [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped), feel free to do so. 

## Usage

- Copy the `blazor.d.ts` file to your project, where you usually hold your typings.
- Either:
	- add a dependency in your TypeScript/JavaScript project to [`@microsoft/signalr`](https://www.npmjs.com/package/@microsoft/signalr),
	- or replace the imports for `HubConnection` and `HubConnectionBuilder` with:
		```ts
		declare type HubConnection: any;
		declare type HubConnectionBuilder: any;
		```
- You can then reference or modify the typings to fit your scenario, for example:
	- If you use modules, you can `export` the types you need.
	- If you just want the `Blazor` object be available ambiently on `window`, declare it in your project:
	  ```ts
	  declare global {
	    const Blazor: IBlazorWeb | IBlazorWebWebAssembly | IBlazorWebServer | IBlazorWebSsr; // Pick your framework
	  }
	  ```
- Code away 🚀🚀🚀

## Warranties
None.