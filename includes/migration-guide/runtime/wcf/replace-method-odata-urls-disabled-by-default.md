---
ms.openlocfilehash: 6dc3669433804a4524c18d5a932f9879343ab508
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235244"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="28b07-101">Nahraďte metodu v adresách URL OData je ve výchozím nastavení zakázána.</span><span class="sxs-lookup"><span data-stu-id="28b07-101">The Replace method in OData URLs is disabled by default</span></span>

|   |   |
|---|---|
|<span data-ttu-id="28b07-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="28b07-102">Details</span></span>|<span data-ttu-id="28b07-103">Počínaje rozhraním .NET Framework 4.5, nahraďte metodu v adresách URL OData je standardně zakázáno.</span><span class="sxs-lookup"><span data-stu-id="28b07-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="28b07-104">Pokud nahradit OData je zakázáno (nyní ve výchozím nastavení), veškeré žádosti uživatelů, včetně funkcí nahradit, (které neobvyklé) se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="28b07-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>|
|<span data-ttu-id="28b07-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="28b07-105">Suggestion</span></span>|<span data-ttu-id="28b07-106">Pokud je potřeba nahradit – metoda (což je běžné), může být znovu zapnout pomocí nastavení konfigurace (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>).</span><span class="sxs-lookup"><span data-stu-id="28b07-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>).</span></span> <span data-ttu-id="28b07-107">Metodu povoleno nahradit však můžete otevřít bezpečnostní zranitelná místa a by měla sloužit pouze po pečlivou revizi.</span><span class="sxs-lookup"><span data-stu-id="28b07-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>|
|<span data-ttu-id="28b07-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="28b07-108">Scope</span></span>|<span data-ttu-id="28b07-109">Edge</span><span class="sxs-lookup"><span data-stu-id="28b07-109">Edge</span></span>|
|<span data-ttu-id="28b07-110">Version</span><span class="sxs-lookup"><span data-stu-id="28b07-110">Version</span></span>|<span data-ttu-id="28b07-111">4.5</span><span class="sxs-lookup"><span data-stu-id="28b07-111">4.5</span></span>|
|<span data-ttu-id="28b07-112">Type</span><span class="sxs-lookup"><span data-stu-id="28b07-112">Type</span></span>|<span data-ttu-id="28b07-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="28b07-113">Runtime</span></span>|
|<span data-ttu-id="28b07-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="28b07-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
