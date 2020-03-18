---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522695"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="79229-101">SPA: SpaServices a NodeServices již nespadají zpět do konzoly logger</span><span class="sxs-lookup"><span data-stu-id="79229-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="79229-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType>a <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> nebude zobrazovat protokoly konzoly, pokud není nakonfigurováno protokolování.</span><span class="sxs-lookup"><span data-stu-id="79229-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="79229-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="79229-103">Version introduced</span></span>

<span data-ttu-id="79229-104">3.0</span><span class="sxs-lookup"><span data-stu-id="79229-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="79229-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="79229-105">Old behavior</span></span>

<span data-ttu-id="79229-106">`Microsoft.AspNetCore.SpaServices`a `Microsoft.AspNetCore.NodeServices` slouží k automatickému vytvoření protokolování konzoly, když protokolování není nakonfigurováno.</span><span class="sxs-lookup"><span data-stu-id="79229-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="79229-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="79229-107">New behavior</span></span>

<span data-ttu-id="79229-108">`Microsoft.AspNetCore.SpaServices`a `Microsoft.AspNetCore.NodeServices` nebude zobrazovat protokoly konzoly, pokud není nakonfigurováno protokolování.</span><span class="sxs-lookup"><span data-stu-id="79229-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="79229-109">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="79229-109">Reason for change</span></span>

<span data-ttu-id="79229-110">Je třeba zarovnat s tím, jak ostatní balíčky ASP.NET Core implementují protokolování.</span><span class="sxs-lookup"><span data-stu-id="79229-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="79229-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="79229-111">Recommended action</span></span>

<span data-ttu-id="79229-112">Pokud je vyžadováno staré chování, chcete-li nakonfigurovat protokolování konzoly, přidejte `services.AddLogging(builder => builder.AddConsole())` `Setup.ConfigureServices` metodu.</span><span class="sxs-lookup"><span data-stu-id="79229-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="79229-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="79229-113">Category</span></span>

<span data-ttu-id="79229-114">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="79229-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="79229-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="79229-115">Affected APIs</span></span>

<span data-ttu-id="79229-116">Žádný</span><span class="sxs-lookup"><span data-stu-id="79229-116">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
