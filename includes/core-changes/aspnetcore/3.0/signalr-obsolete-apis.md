---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394463"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a>SignalR: Metody UseSignalR a UseConnections označené jako zastaralé

Metody `UseConnections` a `UseSignalR` a `ConnectionsRouteBuilder` třídy a `HubRouteBuilder` jsou označeny jako zastaralé v ASP.NET Core 3.0.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Směrování rozbočovače `UseSignalR` `UseConnections`SignalR bylo nakonfigurováno pomocí nebo .

#### <a name="new-behavior"></a>Nové chování

Starý způsob konfigurace směrování byl zastaralý a nahrazen směrováním koncových bodů.

#### <a name="reason-for-change"></a>Důvod změny

Middleware je přesouván do nového systému směrování koncových bodů. Starý způsob přidávání middleware je zastaralý.

#### <a name="recommended-action"></a>Doporučená akce

Nahradit `UseSignalR` `UseEndpoints`:

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

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})`
- `M:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})`
- `T:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder`
- `T:Microsoft.AspNetCore.SignalR.HubRouteBuilder`

-->
