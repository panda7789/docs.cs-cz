---
ms.openlocfilehash: 80d4bbbfe52ab9685d7ca54f21b80d4b1773da22
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859636"
---
### <a name="webclientcancelasync-doesnt-always-cancel-immediately"></a><span data-ttu-id="1efb9-101">WebClient. CancelAsync nevždycky zruší hned</span><span class="sxs-lookup"><span data-stu-id="1efb9-101">WebClient.CancelAsync doesn't always cancel immediately</span></span>

<span data-ttu-id="1efb9-102">Počínaje rozhraním .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> volání neruší žádost okamžitě, pokud se odpověď začala načíst.</span><span class="sxs-lookup"><span data-stu-id="1efb9-102">Starting in .NET Core 2.0, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> doesn't cancel the request immediately if the response has started to fetch.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1efb9-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="1efb9-103">Change description</span></span>

<span data-ttu-id="1efb9-104">Dříve volání <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> zrušilo požadavek okamžitě.</span><span class="sxs-lookup"><span data-stu-id="1efb9-104">Previously, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> canceled the request immediately.</span></span> <span data-ttu-id="1efb9-105">Počínaje rozhraním .NET Core 2,0 volání <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> zruší žádost okamžitě pouze v případě, že se odpověď nezačala načítat.</span><span class="sxs-lookup"><span data-stu-id="1efb9-105">Starting in .NET Core 2.0, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> cancels the request immediately only if the response hasn't started fetching.</span></span> <span data-ttu-id="1efb9-106">Pokud se odpověď začala načítat, žádost se zruší až po načtení kompletní odpovědi.</span><span class="sxs-lookup"><span data-stu-id="1efb9-106">If the response has started to fetch, the request is cancelled only after a complete response is read.</span></span>

<span data-ttu-id="1efb9-107">Tato změna byla implementována, <xref:System.Net.WebClient> protože rozhraní API je namísto toho zastaralé <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="1efb9-107">This change was implemented because the <xref:System.Net.WebClient> API is deprecated in favor of <xref:System.Net.Http.HttpClient>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1efb9-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="1efb9-108">Version introduced</span></span>

<span data-ttu-id="1efb9-109">2.0</span><span class="sxs-lookup"><span data-stu-id="1efb9-109">2.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1efb9-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="1efb9-110">Recommended action</span></span>

<span data-ttu-id="1efb9-111">Místo toho <xref:System.Net.Http.HttpClient?displayProperty=fullName> použijte třídu <xref:System.Net.WebClient?displayProperty=fullName>, která je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="1efb9-111">Use the <xref:System.Net.Http.HttpClient?displayProperty=fullName> class instead of <xref:System.Net.WebClient?displayProperty=fullName>, which is deprecated.</span></span>

#### <a name="category"></a><span data-ttu-id="1efb9-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="1efb9-112">Category</span></span>

<span data-ttu-id="1efb9-113">Sítě</span><span class="sxs-lookup"><span data-stu-id="1efb9-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1efb9-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1efb9-114">Affected APIs</span></span>

- <xref:System.Net.WebClient.CancelAsync?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.WebClient.CancelAsync`

-->
