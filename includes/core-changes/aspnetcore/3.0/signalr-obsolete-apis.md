---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394463"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a><span data-ttu-id="2316c-101">Signál: metody UseSignalR a UseConnections označené jako zastaralé</span><span class="sxs-lookup"><span data-stu-id="2316c-101">SignalR: UseSignalR and UseConnections methods marked obsolete</span></span>

<span data-ttu-id="2316c-102">Metody `UseConnections` a `UseSignalR` a třídy `ConnectionsRouteBuilder` a `HubRouteBuilder` jsou v ASP.NET Core 3,0 označeny jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="2316c-102">The methods `UseConnections` and `UseSignalR` and the classes `ConnectionsRouteBuilder` and `HubRouteBuilder` are marked as obsolete in ASP.NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2316c-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="2316c-103">Version introduced</span></span>

<span data-ttu-id="2316c-104">3.0</span><span class="sxs-lookup"><span data-stu-id="2316c-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2316c-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="2316c-105">Old behavior</span></span>

<span data-ttu-id="2316c-106">Směrování centra signalizace bylo nakonfigurováno pomocí `UseSignalR` nebo `UseConnections`.</span><span class="sxs-lookup"><span data-stu-id="2316c-106">SignalR hub routing was configured using `UseSignalR` or `UseConnections`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2316c-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="2316c-107">New behavior</span></span>

<span data-ttu-id="2316c-108">Starý způsob konfigurace směrování se zastaral a nahradil směrováním koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="2316c-108">The old way of configuring routing has been obsoleted and replaced with endpoint routing.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2316c-109">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="2316c-109">Reason for change</span></span>

<span data-ttu-id="2316c-110">Middleware se přesouvá do nového systému směrování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="2316c-110">Middleware is being moved to the new endpoint routing system.</span></span> <span data-ttu-id="2316c-111">Starý způsob přidávání middlewaru je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="2316c-111">The old way of adding middleware is being obsoleted.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2316c-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="2316c-112">Recommended action</span></span>

<span data-ttu-id="2316c-113">Nahraďte `UseSignalR` pomocí `UseEndpoints`:</span><span class="sxs-lookup"><span data-stu-id="2316c-113">Replace `UseSignalR` with `UseEndpoints`:</span></span>

<span data-ttu-id="2316c-114">**Starý kód:**</span><span class="sxs-lookup"><span data-stu-id="2316c-114">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="2316c-115">**Nový kód:**</span><span class="sxs-lookup"><span data-stu-id="2316c-115">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a><span data-ttu-id="2316c-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="2316c-116">Category</span></span>

<span data-ttu-id="2316c-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2316c-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2316c-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2316c-118">Affected APIs</span></span>

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
