---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394196"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="f5570-101">Poštolka: Transport abstrakce odstraněny a zveřejněny</span><span class="sxs-lookup"><span data-stu-id="f5570-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="f5570-102">Jako součást odklonu od "pubternal" rozhraní API kestrel transportní vrstvy rozhraní `Microsoft.AspNetCore.Connections.Abstractions` jsou vystaveny jako veřejné rozhraní v knihovně.</span><span class="sxs-lookup"><span data-stu-id="f5570-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f5570-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="f5570-103">Version introduced</span></span>

<span data-ttu-id="f5570-104">3.0</span><span class="sxs-lookup"><span data-stu-id="f5570-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f5570-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="f5570-105">Old behavior</span></span>

- <span data-ttu-id="f5570-106">Abstrakce související s dopravou `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` byly k dispozici v knihovně.</span><span class="sxs-lookup"><span data-stu-id="f5570-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="f5570-107">Nemovitost `ListenOptions.NoDelay` byla k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f5570-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f5570-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="f5570-108">New behavior</span></span>

- <span data-ttu-id="f5570-109">Rozhraní `IConnectionListener` bylo zavedeno `Microsoft.AspNetCore.Connections.Abstractions` v knihovně vystavit nejpoužívanější `...Transport.Abstractions` funkce z knihovny.</span><span class="sxs-lookup"><span data-stu-id="f5570-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="f5570-110">The `NoDelay` je nyní k`LibuvTransportOptions` dispozici `SocketTransportOptions`v možnostech dopravy ( a ).</span><span class="sxs-lookup"><span data-stu-id="f5570-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="f5570-111">`SchedulingMode`již není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f5570-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f5570-112">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="f5570-112">Reason for change</span></span>

<span data-ttu-id="f5570-113">ASP.NET Core 3.0 se odklonil od "pubternal" API.</span><span class="sxs-lookup"><span data-stu-id="f5570-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f5570-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="f5570-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="f5570-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="f5570-115">Category</span></span>

<span data-ttu-id="f5570-116">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f5570-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f5570-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f5570-117">Affected APIs</span></span>

<span data-ttu-id="f5570-118">Žádný</span><span class="sxs-lookup"><span data-stu-id="f5570-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
