---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394463"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a><span data-ttu-id="ef730-101">SignalR: Metody UseSignalR a UseConnections označené jako zastaralé</span><span class="sxs-lookup"><span data-stu-id="ef730-101">SignalR: UseSignalR and UseConnections methods marked obsolete</span></span>

<span data-ttu-id="ef730-102">Metody `UseConnections` a `UseSignalR` a `ConnectionsRouteBuilder` třídy a `HubRouteBuilder` jsou označeny jako zastaralé v ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ef730-102">The methods `UseConnections` and `UseSignalR` and the classes `ConnectionsRouteBuilder` and `HubRouteBuilder` are marked as obsolete in ASP.NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ef730-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="ef730-103">Version introduced</span></span>

<span data-ttu-id="ef730-104">3.0</span><span class="sxs-lookup"><span data-stu-id="ef730-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ef730-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="ef730-105">Old behavior</span></span>

<span data-ttu-id="ef730-106">Směrování rozbočovače `UseSignalR` `UseConnections`SignalR bylo nakonfigurováno pomocí nebo .</span><span class="sxs-lookup"><span data-stu-id="ef730-106">SignalR hub routing was configured using `UseSignalR` or `UseConnections`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ef730-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="ef730-107">New behavior</span></span>

<span data-ttu-id="ef730-108">Starý způsob konfigurace směrování byl zastaralý a nahrazen směrováním koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="ef730-108">The old way of configuring routing has been obsoleted and replaced with endpoint routing.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ef730-109">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="ef730-109">Reason for change</span></span>

<span data-ttu-id="ef730-110">Middleware je přesouván do nového systému směrování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="ef730-110">Middleware is being moved to the new endpoint routing system.</span></span> <span data-ttu-id="ef730-111">Starý způsob přidávání middleware je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="ef730-111">The old way of adding middleware is being obsoleted.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ef730-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="ef730-112">Recommended action</span></span>

<span data-ttu-id="ef730-113">Nahradit `UseSignalR` `UseEndpoints`:</span><span class="sxs-lookup"><span data-stu-id="ef730-113">Replace `UseSignalR` with `UseEndpoints`:</span></span>

<span data-ttu-id="ef730-114">**Starý kód:**</span><span class="sxs-lookup"><span data-stu-id="ef730-114">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="ef730-115">**Nový kód:**</span><span class="sxs-lookup"><span data-stu-id="ef730-115">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a><span data-ttu-id="ef730-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="ef730-116">Category</span></span>

<span data-ttu-id="ef730-117">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ef730-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ef730-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ef730-118">Affected APIs</span></span>

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
