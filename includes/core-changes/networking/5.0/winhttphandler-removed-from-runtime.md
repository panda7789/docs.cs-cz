---
ms.openlocfilehash: 115cd6be935ae12a1293f948a0f899c6c3ff0d78
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608472"
---
### <a name="winhttphandler-removed-from-net-runtime"></a><span data-ttu-id="be46f-101">WinHttpHandler odebrané z modulu runtime .NET</span><span class="sxs-lookup"><span data-stu-id="be46f-101">WinHttpHandler removed from .NET runtime</span></span>

<span data-ttu-id="be46f-102">`WinHttpHandler`Třída byla odebrána z *System.Net.Http.dll* sestavení.</span><span class="sxs-lookup"><span data-stu-id="be46f-102">The `WinHttpHandler` class was removed from the *System.Net.Http.dll* assembly.</span></span> <span data-ttu-id="be46f-103">Je teď dostupná jenom jako [balíček NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)pro vzdálenou správu (OOB).</span><span class="sxs-lookup"><span data-stu-id="be46f-103">It's now available only as an out-of-band (OOB) [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="be46f-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="be46f-104">Version introduced</span></span>

<span data-ttu-id="be46f-105">5.0</span><span class="sxs-lookup"><span data-stu-id="be46f-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="be46f-106">Popis změny</span><span class="sxs-lookup"><span data-stu-id="be46f-106">Change description</span></span>

<span data-ttu-id="be46f-107">V předchozích verzích .NET <xref:System.Net.Http.WinHttpHandler> je třída k dispozici jako součást základních knihoven .NET.</span><span class="sxs-lookup"><span data-stu-id="be46f-107">In previous .NET versions, the <xref:System.Net.Http.WinHttpHandler> class is available as part of the core .NET libraries.</span></span> <span data-ttu-id="be46f-108">Počínaje platformou .NET 5,0 <xref:System.Net.Http.WinHttpHandler> je třída k dispozici pouze jako samostatně instalovaný [balíček NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span><span class="sxs-lookup"><span data-stu-id="be46f-108">Starting in .NET 5.0, the <xref:System.Net.Http.WinHttpHandler> class is only available as a separately installed [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="be46f-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="be46f-109">Recommended action</span></span>

<span data-ttu-id="be46f-110">Nainstalujte [balíček NuGet System .NET. http. WinHttpHandler](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span><span class="sxs-lookup"><span data-stu-id="be46f-110">Install the [System.Net.Http.WinHttpHandler NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span> <span data-ttu-id="be46f-111">Nebo pokud nepotřebujete funkce specifické pro službu WinHTTP, použijte <xref:System.Net.Http.SocketsHttpHandler> místo toho.</span><span class="sxs-lookup"><span data-stu-id="be46f-111">Or, if you don't require WinHTTP-specific features, use <xref:System.Net.Http.SocketsHttpHandler> instead.</span></span>

#### <a name="category"></a><span data-ttu-id="be46f-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="be46f-112">Category</span></span>

<span data-ttu-id="be46f-113">Sítě</span><span class="sxs-lookup"><span data-stu-id="be46f-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="be46f-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="be46f-114">Affected APIs</span></span>

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

-->
