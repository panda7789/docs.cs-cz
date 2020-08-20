---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291646"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="4f087-101">Signál: metody UseSignalR a UseConnections se odebraly.</span><span class="sxs-lookup"><span data-stu-id="4f087-101">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="4f087-102">V ASP.NET Core 3,0 vydaný signál přijal směrování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4f087-102">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="4f087-103">V rámci této změny <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A> byly, a některé související metody označeny jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="4f087-103">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="4f087-104">V ASP.NET Core 5,0 byly odebrány zastaralé metody.</span><span class="sxs-lookup"><span data-stu-id="4f087-104">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="4f087-105">Úplný seznam metod najdete v tématu [ovlivněná rozhraní API](#affected-apis).</span><span class="sxs-lookup"><span data-stu-id="4f087-105">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="4f087-106">Diskuzi o tomto problému najdete v tématu [dotnet/aspnetcore # 20082](https://github.com/dotnet/aspnetcore/issues/20082).</span><span class="sxs-lookup"><span data-stu-id="4f087-106">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4f087-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="4f087-107">Version introduced</span></span>

<span data-ttu-id="4f087-108">5,0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="4f087-108">5.0 Preview 3</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4f087-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="4f087-109">Old behavior</span></span>

<span data-ttu-id="4f087-110">Centra a obslužné rutiny připojení můžou být v kanálu middleware registrovány pomocí `UseSignalR` `UseConnections` metod nebo.</span><span class="sxs-lookup"><span data-stu-id="4f087-110">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4f087-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="4f087-111">New behavior</span></span>

<span data-ttu-id="4f087-112">Centra signálů a obslužné rutiny připojení by měly být zaregistrované v rámci <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> použití <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> rozšiřujících metod a <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder> .</span><span class="sxs-lookup"><span data-stu-id="4f087-112">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4f087-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="4f087-113">Reason for change</span></span>

<span data-ttu-id="4f087-114">Staré metody měly vlastní logiku směrování, která nespolupracovala s ostatními součástmi směrování v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4f087-114">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="4f087-115">V ASP.NET Core 3,0 byla představena nová služba směrování pro obecné účely, která se nazývá směrování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4f087-115">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="4f087-116">Signál s povoleným směrováním koncových bodů pro interakci s ostatními součástmi směrování.</span><span class="sxs-lookup"><span data-stu-id="4f087-116">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="4f087-117">Přepnutím na tento model umožníte uživatelům realizovat všechny výhody směrování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="4f087-117">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="4f087-118">Proto byly staré metody odebrány.</span><span class="sxs-lookup"><span data-stu-id="4f087-118">Consequently, the old methods have been removed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4f087-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="4f087-119">Recommended action</span></span>

<span data-ttu-id="4f087-120">Odeberte kód, který volá `UseSignalR` nebo `UseConnections` z metody vašeho projektu `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="4f087-120">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="4f087-121">Nahraďte je voláním `MapHub` nebo `MapConnectionHandler` v rámci těla volání `UseEndpoints` .</span><span class="sxs-lookup"><span data-stu-id="4f087-121">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="4f087-122">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4f087-122">For example:</span></span>

<span data-ttu-id="4f087-123">**Starý kód:**</span><span class="sxs-lookup"><span data-stu-id="4f087-123">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="4f087-124">**Nový kód:**</span><span class="sxs-lookup"><span data-stu-id="4f087-124">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="4f087-125">Obecně platí, že vaše předchozí `MapHub` a `MapConnectionHandler` volání lze přenést přímo z těla `UseSignalR` a `UseConnections` na `UseEndpoints` s nepotřebnou změnou.</span><span class="sxs-lookup"><span data-stu-id="4f087-125">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

#### <a name="category"></a><span data-ttu-id="4f087-126">Kategorie</span><span class="sxs-lookup"><span data-stu-id="4f087-126">Category</span></span>

<span data-ttu-id="4f087-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4f087-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4f087-128">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4f087-128">Affected APIs</span></span>

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
