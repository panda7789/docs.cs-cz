---
ms.openlocfilehash: fb23418816abcae125106c93b339a546aa9bc2ee
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721182"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="dff87-101">Kestrel: abstrakce přenosu se odebrala a provedla jako veřejná.</span><span class="sxs-lookup"><span data-stu-id="dff87-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="dff87-102">V rámci přesunu z rozhraní API přenosové vrstvy pubternal se rozhraní API transportní vrstvy Kestrel zveřejňují jako veřejné rozhraní v `Microsoft.AspNetCore.Connections.Abstractions` knihovně.</span><span class="sxs-lookup"><span data-stu-id="dff87-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dff87-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="dff87-103">Version introduced</span></span>

<span data-ttu-id="dff87-104">3.0</span><span class="sxs-lookup"><span data-stu-id="dff87-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="dff87-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="dff87-105">Old behavior</span></span>

- <span data-ttu-id="dff87-106">V knihovně jsou k dispozici abstrakce související s přenosem `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` .</span><span class="sxs-lookup"><span data-stu-id="dff87-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="dff87-107">`ListenOptions.NoDelay`Vlastnost byla k dispozici.</span><span class="sxs-lookup"><span data-stu-id="dff87-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="dff87-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="dff87-108">New behavior</span></span>

- <span data-ttu-id="dff87-109">`IConnectionListener`Rozhraní bylo představeno v `Microsoft.AspNetCore.Connections.Abstractions` knihovně, aby bylo možné vystavit z knihovny nejčastěji používané funkce `...Transport.Abstractions` .</span><span class="sxs-lookup"><span data-stu-id="dff87-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="dff87-110">`NoDelay`Je nyní k dispozici v možnostech přenosu ( `LibuvTransportOptions` a `SocketTransportOptions` ).</span><span class="sxs-lookup"><span data-stu-id="dff87-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="dff87-111">`SchedulingMode`již není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="dff87-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="dff87-112">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="dff87-112">Reason for change</span></span>

<span data-ttu-id="dff87-113">ASP.NET Core 3,0 se přesunuly z rozhraní API "pubternal".</span><span class="sxs-lookup"><span data-stu-id="dff87-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dff87-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="dff87-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="dff87-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="dff87-115">Category</span></span>

<span data-ttu-id="dff87-116">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dff87-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dff87-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="dff87-117">Affected APIs</span></span>

<span data-ttu-id="dff87-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="dff87-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
