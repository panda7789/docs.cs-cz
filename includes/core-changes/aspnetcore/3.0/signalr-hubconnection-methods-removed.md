---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901919"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="4aa80-101">SignalR: Metody ResetSendPing a ResetTimeout připojení hubu byly odebrány</span><span class="sxs-lookup"><span data-stu-id="4aa80-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="4aa80-102">Metody `ResetSendPing` `ResetTimeout` a byly odebrány `HubConnection` z rozhraní API signalr.</span><span class="sxs-lookup"><span data-stu-id="4aa80-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="4aa80-103">Tyto metody byly původně určeny pouze pro vnitřní použití, ale byly zveřejněny v ASP.NET core 2.2.</span><span class="sxs-lookup"><span data-stu-id="4aa80-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="4aa80-104">Tyto metody nebudou k dispozici počínaje ASP.NET verze Core 3.0 Preview 4.</span><span class="sxs-lookup"><span data-stu-id="4aa80-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="4aa80-105">Diskuse naleznete [v tématu dotnet/aspnetcore#8543](https://github.com/dotnet/aspnetcore/issues/8543).</span><span class="sxs-lookup"><span data-stu-id="4aa80-105">For discussion, see [dotnet/aspnetcore#8543](https://github.com/dotnet/aspnetcore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4aa80-106">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="4aa80-106">Version introduced</span></span>

<span data-ttu-id="4aa80-107">3.0</span><span class="sxs-lookup"><span data-stu-id="4aa80-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4aa80-108">Staré chování</span><span class="sxs-lookup"><span data-stu-id="4aa80-108">Old behavior</span></span>

<span data-ttu-id="4aa80-109">K dispozici byla rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="4aa80-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4aa80-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="4aa80-110">New behavior</span></span>

<span data-ttu-id="4aa80-111">Api jsou odebrány.</span><span class="sxs-lookup"><span data-stu-id="4aa80-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4aa80-112">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="4aa80-112">Reason for change</span></span>

<span data-ttu-id="4aa80-113">Tyto metody byly původně určeny pouze pro vnitřní použití, ale byly zveřejněny v ASP.NET core 2.2.</span><span class="sxs-lookup"><span data-stu-id="4aa80-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4aa80-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="4aa80-114">Recommended action</span></span>

<span data-ttu-id="4aa80-115">Nepoužívejte tyto metody.</span><span class="sxs-lookup"><span data-stu-id="4aa80-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="4aa80-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="4aa80-116">Category</span></span>

<span data-ttu-id="4aa80-117">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4aa80-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4aa80-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4aa80-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
