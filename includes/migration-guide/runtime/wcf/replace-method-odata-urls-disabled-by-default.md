---
ms.openlocfilehash: 6dc3669433804a4524c18d5a932f9879343ab508
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803644"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="ff63b-101">Nahraďte metodu v adresách URL OData je ve výchozím nastavení zakázána.</span><span class="sxs-lookup"><span data-stu-id="ff63b-101">The Replace method in OData URLs is disabled by default</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ff63b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ff63b-102">Details</span></span>|<span data-ttu-id="ff63b-103">Počínaje rozhraním .NET Framework 4.5, nahraďte metodu v adresách URL OData je standardně zakázáno.</span><span class="sxs-lookup"><span data-stu-id="ff63b-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="ff63b-104">Pokud nahradit OData je zakázáno (nyní ve výchozím nastavení), veškeré žádosti uživatelů, včetně funkcí nahradit, (které neobvyklé) se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="ff63b-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>|
|<span data-ttu-id="ff63b-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="ff63b-105">Suggestion</span></span>|<span data-ttu-id="ff63b-106">Pokud je potřeba nahradit – metoda (což je běžné), může být znovu zapnout pomocí nastavení konfigurace (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>).</span><span class="sxs-lookup"><span data-stu-id="ff63b-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>).</span></span> <span data-ttu-id="ff63b-107">Metodu povoleno nahradit však můžete otevřít bezpečnostní zranitelná místa a by měla sloužit pouze po pečlivou revizi.</span><span class="sxs-lookup"><span data-stu-id="ff63b-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>|
|<span data-ttu-id="ff63b-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ff63b-108">Scope</span></span>|<span data-ttu-id="ff63b-109">Edge</span><span class="sxs-lookup"><span data-stu-id="ff63b-109">Edge</span></span>|
|<span data-ttu-id="ff63b-110">Version</span><span class="sxs-lookup"><span data-stu-id="ff63b-110">Version</span></span>|<span data-ttu-id="ff63b-111">4.5</span><span class="sxs-lookup"><span data-stu-id="ff63b-111">4.5</span></span>|
|<span data-ttu-id="ff63b-112">Type</span><span class="sxs-lookup"><span data-stu-id="ff63b-112">Type</span></span>|<span data-ttu-id="ff63b-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="ff63b-113">Runtime</span></span>|
|<span data-ttu-id="ff63b-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ff63b-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
