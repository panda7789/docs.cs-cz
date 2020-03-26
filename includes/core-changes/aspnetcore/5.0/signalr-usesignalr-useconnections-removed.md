---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291646"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a>SignalR: UseSignalR a UseConnections metody odebrány

V ASP.NET Core 3.0 přijal signalr směrování koncových bodů. V rámci této změny <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>byly a některé související metody označeny jako zastaralé. V ASP.NET Core 5.0 byly tyto zastaralé metody odstraněny. Úplný seznam metod naleznete [v tématu Ovlivněná api](#affected-apis).

Diskuse o tomto problému naleznete [v tématu dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).

#### <a name="version-introduced"></a>Zavedená verze

5.0 Náhled 3

#### <a name="old-behavior"></a>Staré chování

Rozbočovače SignalR a obslužné rutiny připojení mohou být registrovány v kanálu middlewaru `UseSignalR` pomocí metod nebo. `UseConnections`

#### <a name="new-behavior"></a>Nové chování

Rozbočovače SignalR a obslužné rutiny připojení by měly být registrovány <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> v rámci metody <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> a <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> rozšíření na <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.

#### <a name="reason-for-change"></a>Důvod změny

Staré metody měly vlastní logiku směrování, která nekomunikovala s jinými součástmi směrování v ASP.NET Jádra. V ASP.NET Core 3.0 byl zaveden nový univerzální směrovací systém, nazývaný směrování koncových bodů. Směrování koncového bodu povoleno SignalR pro interakci s ostatními součástmi směrování. Přechod na tento model umožňuje uživatelům realizovat všechny výhody směrování koncových bodů. V důsledku toho byly staré metody odstraněny.

#### <a name="recommended-action"></a>Doporučená akce

Odeberte `UseSignalR` kód, který volá nebo `UseConnections` z `Startup.Configure` metody projektu. Nahraďte jej `MapHub` `MapConnectionHandler`voláním nebo , v těle `UseEndpoints`volání . Například:

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

Obecně platí, `MapHub` že `MapConnectionHandler` vaše předchozí hovory a hovory `UseSignalR` `UseConnections` mohou `UseEndpoints` být převedeny přímo z těla a s malou-k-žádné změny potřebné.

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
