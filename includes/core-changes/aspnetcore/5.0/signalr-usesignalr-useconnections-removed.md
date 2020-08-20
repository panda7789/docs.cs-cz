---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291646"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a>Signál: metody UseSignalR a UseConnections se odebraly.

V ASP.NET Core 3,0 vydaný signál přijal směrování koncového bodu. V rámci této změny <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A> byly, a některé související metody označeny jako zastaralé. V ASP.NET Core 5,0 byly odebrány zastaralé metody. Úplný seznam metod najdete v tématu [ovlivněná rozhraní API](#affected-apis).

Diskuzi o tomto problému najdete v tématu [dotnet/aspnetcore # 20082](https://github.com/dotnet/aspnetcore/issues/20082).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 3

#### <a name="old-behavior"></a>Staré chování

Centra a obslužné rutiny připojení můžou být v kanálu middleware registrovány pomocí `UseSignalR` `UseConnections` metod nebo.

#### <a name="new-behavior"></a>Nové chování

Centra signálů a obslužné rutiny připojení by měly být zaregistrované v rámci <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> použití <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> rozšiřujících metod a <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder> .

#### <a name="reason-for-change"></a>Důvod změny

Staré metody měly vlastní logiku směrování, která nespolupracovala s ostatními součástmi směrování v ASP.NET Core. V ASP.NET Core 3,0 byla představena nová služba směrování pro obecné účely, která se nazývá směrování koncového bodu. Signál s povoleným směrováním koncových bodů pro interakci s ostatními součástmi směrování. Přepnutím na tento model umožníte uživatelům realizovat všechny výhody směrování koncových bodů. Proto byly staré metody odebrány.

#### <a name="recommended-action"></a>Doporučená akce

Odeberte kód, který volá `UseSignalR` nebo `UseConnections` z metody vašeho projektu `Startup.Configure` . Nahraďte je voláním `MapHub` nebo `MapConnectionHandler` v rámci těla volání `UseEndpoints` . Příklad:

**Starý kód:**

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

**Nový kód:**

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

Obecně platí, že vaše předchozí `MapHub` a `MapConnectionHandler` volání lze přenést přímo z těla `UseSignalR` a `UseConnections` na `UseEndpoints` s nepotřebnou změnou.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->
