---
ms.openlocfilehash: 1017801346e65940e4dc075ef72f7a00d7e6bcd9
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393959"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="2a38a-101">Jednostránkové: SpaServices a NodeServices se už nevrátí do protokolovacího nástroje konzoly.</span><span class="sxs-lookup"><span data-stu-id="2a38a-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="2a38a-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> a <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> nezobrazí protokoly konzoly, pokud není nakonfigurováno protokolování.</span><span class="sxs-lookup"><span data-stu-id="2a38a-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2a38a-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="2a38a-103">Version introduced</span></span>

<span data-ttu-id="2a38a-104">3.0</span><span class="sxs-lookup"><span data-stu-id="2a38a-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2a38a-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="2a38a-105">Old behavior</span></span>

<span data-ttu-id="2a38a-106">`Microsoft.AspNetCore.SpaServices` a `Microsoft.AspNetCore.NodeServices` slouží k automatickému vytvoření protokolovacího nástroje konzoly, pokud není nakonfigurováno protokolování.</span><span class="sxs-lookup"><span data-stu-id="2a38a-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span> 

#### <a name="new-behavior"></a><span data-ttu-id="2a38a-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="2a38a-107">New behavior</span></span>

<span data-ttu-id="2a38a-108">`Microsoft.AspNetCore.SpaServices` a `Microsoft.AspNetCore.NodeServices` nezobrazí protokoly konzoly, pokud není nakonfigurováno protokolování.</span><span class="sxs-lookup"><span data-stu-id="2a38a-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2a38a-109">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="2a38a-109">Reason for change</span></span>

<span data-ttu-id="2a38a-110">Je potřeba se zarovnávat s tím, jak jiné balíčky ASP.NET Core implementují protokolování.</span><span class="sxs-lookup"><span data-stu-id="2a38a-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2a38a-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="2a38a-111">Recommended action</span></span>

<span data-ttu-id="2a38a-112">Pokud je nutné staré chování, nakonfigurujte protokolování konzoly přidáním `services.AddLogging(builder => builder.AddConsole())` do metody `Setup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="2a38a-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="2a38a-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="2a38a-113">Category</span></span>

<span data-ttu-id="2a38a-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2a38a-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2a38a-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2a38a-115">Affected APIs</span></span>

<span data-ttu-id="2a38a-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="2a38a-116">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
