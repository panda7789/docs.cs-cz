---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291646"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="25158-101">SignalR: UseSignalR a UseConnections metody odebrány</span><span class="sxs-lookup"><span data-stu-id="25158-101">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="25158-102">V ASP.NET Core 3.0 přijal signalr směrování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="25158-102">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="25158-103">V rámci této změny <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>byly a některé související metody označeny jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="25158-103">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="25158-104">V ASP.NET Core 5.0 byly tyto zastaralé metody odstraněny.</span><span class="sxs-lookup"><span data-stu-id="25158-104">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="25158-105">Úplný seznam metod naleznete [v tématu Ovlivněná api](#affected-apis).</span><span class="sxs-lookup"><span data-stu-id="25158-105">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="25158-106">Diskuse o tomto problému naleznete [v tématu dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span><span class="sxs-lookup"><span data-stu-id="25158-106">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="25158-107">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="25158-107">Version introduced</span></span>

<span data-ttu-id="25158-108">5.0 Náhled 3</span><span class="sxs-lookup"><span data-stu-id="25158-108">5.0 Preview 3</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="25158-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="25158-109">Old behavior</span></span>

<span data-ttu-id="25158-110">Rozbočovače SignalR a obslužné rutiny připojení mohou být registrovány v kanálu middlewaru `UseSignalR` pomocí metod nebo. `UseConnections`</span><span class="sxs-lookup"><span data-stu-id="25158-110">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="25158-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="25158-111">New behavior</span></span>

<span data-ttu-id="25158-112">Rozbočovače SignalR a obslužné rutiny připojení by měly být registrovány <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> v rámci metody <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> a <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> rozšíření na <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span><span class="sxs-lookup"><span data-stu-id="25158-112">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="25158-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="25158-113">Reason for change</span></span>

<span data-ttu-id="25158-114">Staré metody měly vlastní logiku směrování, která nekomunikovala s jinými součástmi směrování v ASP.NET Jádra.</span><span class="sxs-lookup"><span data-stu-id="25158-114">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="25158-115">V ASP.NET Core 3.0 byl zaveden nový univerzální směrovací systém, nazývaný směrování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="25158-115">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="25158-116">Směrování koncového bodu povoleno SignalR pro interakci s ostatními součástmi směrování.</span><span class="sxs-lookup"><span data-stu-id="25158-116">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="25158-117">Přechod na tento model umožňuje uživatelům realizovat všechny výhody směrování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="25158-117">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="25158-118">V důsledku toho byly staré metody odstraněny.</span><span class="sxs-lookup"><span data-stu-id="25158-118">Consequently, the old methods have been removed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="25158-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="25158-119">Recommended action</span></span>

<span data-ttu-id="25158-120">Odeberte `UseSignalR` kód, který volá nebo `UseConnections` z `Startup.Configure` metody projektu.</span><span class="sxs-lookup"><span data-stu-id="25158-120">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="25158-121">Nahraďte jej `MapHub` `MapConnectionHandler`voláním nebo , v těle `UseEndpoints`volání .</span><span class="sxs-lookup"><span data-stu-id="25158-121">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="25158-122">Například:</span><span class="sxs-lookup"><span data-stu-id="25158-122">For example:</span></span>

<span data-ttu-id="25158-123">**Starý kód:**</span><span class="sxs-lookup"><span data-stu-id="25158-123">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="25158-124">**Nový kód:**</span><span class="sxs-lookup"><span data-stu-id="25158-124">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="25158-125">Obecně platí, `MapHub` že `MapConnectionHandler` vaše předchozí hovory a hovory `UseSignalR` `UseConnections` mohou `UseEndpoints` být převedeny přímo z těla a s malou-k-žádné změny potřebné.</span><span class="sxs-lookup"><span data-stu-id="25158-125">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

#### <a name="category"></a><span data-ttu-id="25158-126">Kategorie</span><span class="sxs-lookup"><span data-stu-id="25158-126">Category</span></span>

<span data-ttu-id="25158-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="25158-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="25158-128">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="25158-128">Affected APIs</span></span>

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
