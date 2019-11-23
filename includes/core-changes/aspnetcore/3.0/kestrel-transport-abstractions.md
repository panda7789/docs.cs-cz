---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394196"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="efd33-101">Kestrel: abstrakce přenosu se odebrala a provedla jako veřejná.</span><span class="sxs-lookup"><span data-stu-id="efd33-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="efd33-102">V rámci přesunu z rozhraní API pro pubternal jsou v knihovně `Microsoft.AspNetCore.Connections.Abstractions` zpřístupněny rozhraní API přenosové vrstvy Kestrel jako veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="efd33-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="efd33-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="efd33-103">Version introduced</span></span>

<span data-ttu-id="efd33-104">3,0</span><span class="sxs-lookup"><span data-stu-id="efd33-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="efd33-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="efd33-105">Old behavior</span></span>

- <span data-ttu-id="efd33-106">V knihovně `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` byly k dispozici abstrakce související s přenosem.</span><span class="sxs-lookup"><span data-stu-id="efd33-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="efd33-107">Vlastnost `ListenOptions.NoDelay` byla k dispozici.</span><span class="sxs-lookup"><span data-stu-id="efd33-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="efd33-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="efd33-108">New behavior</span></span>

- <span data-ttu-id="efd33-109">Rozhraní `IConnectionListener` bylo představeno v knihovně `Microsoft.AspNetCore.Connections.Abstractions`, aby vystavilo nejvíce používané funkce z knihovny `...Transport.Abstractions`.</span><span class="sxs-lookup"><span data-stu-id="efd33-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="efd33-110">`NoDelay` je teď k dispozici v možnostech přenosu (`LibuvTransportOptions` a `SocketTransportOptions`).</span><span class="sxs-lookup"><span data-stu-id="efd33-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="efd33-111">`SchedulingMode` již není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="efd33-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="efd33-112">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="efd33-112">Reason for change</span></span>

<span data-ttu-id="efd33-113">ASP.NET Core 3,0 se přesunuly z rozhraní API "pubternal".</span><span class="sxs-lookup"><span data-stu-id="efd33-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="efd33-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="efd33-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="efd33-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="efd33-115">Category</span></span>

<span data-ttu-id="efd33-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="efd33-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="efd33-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="efd33-117">Affected APIs</span></span>

<span data-ttu-id="efd33-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="efd33-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
