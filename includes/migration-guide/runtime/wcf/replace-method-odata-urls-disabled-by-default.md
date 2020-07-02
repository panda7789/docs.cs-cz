---
ms.openlocfilehash: b2fcacdb02c411c4dcb12051bf0c6759faccdea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620065"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="b5949-101">Metoda Replace v adresách URL OData je ve výchozím nastavení zakázaná.</span><span class="sxs-lookup"><span data-stu-id="b5949-101">The Replace method in OData URLs is disabled by default</span></span>

#### <a name="details"></a><span data-ttu-id="b5949-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b5949-102">Details</span></span>

<span data-ttu-id="b5949-103">Počínaje .NET Framework 4,5 je metoda Replace v adresách URL OData ve výchozím nastavení zakázaná.</span><span class="sxs-lookup"><span data-stu-id="b5949-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="b5949-104">Pokud je nahrazení OData zakázané (teď ve výchozím nastavení), všechny požadavky uživatelů, včetně funkcí nahrazení (které nejsou běžné), selžou.</span><span class="sxs-lookup"><span data-stu-id="b5949-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b5949-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="b5949-105">Suggestion</span></span>

<span data-ttu-id="b5949-106">Pokud je vyžadována metoda Replace (která je neobvyklá), může být znovu povolena prostřednictvím nastavení konfigurace ( <xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="b5949-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>).</span></span> <span data-ttu-id="b5949-107">Povolená metoda Replace ale může otevřít bezpečnostní ohrožení zabezpečení a měla by se používat jenom po pečlivém přezkoumání.</span><span class="sxs-lookup"><span data-stu-id="b5949-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>

| <span data-ttu-id="b5949-108">Name</span><span class="sxs-lookup"><span data-stu-id="b5949-108">Name</span></span>    | <span data-ttu-id="b5949-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b5949-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b5949-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b5949-110">Scope</span></span>   |<span data-ttu-id="b5949-111">Edge</span><span class="sxs-lookup"><span data-stu-id="b5949-111">Edge</span></span>|
|<span data-ttu-id="b5949-112">Verze</span><span class="sxs-lookup"><span data-stu-id="b5949-112">Version</span></span>|<span data-ttu-id="b5949-113">4.5</span><span class="sxs-lookup"><span data-stu-id="b5949-113">4.5</span></span>|
|<span data-ttu-id="b5949-114">Typ</span><span class="sxs-lookup"><span data-stu-id="b5949-114">Type</span></span>|<span data-ttu-id="b5949-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="b5949-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b5949-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b5949-116">Affected APIs</span></span>

-<xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
