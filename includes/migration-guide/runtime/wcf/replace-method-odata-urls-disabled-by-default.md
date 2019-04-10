---
ms.openlocfilehash: 6dc3669433804a4524c18d5a932f9879343ab508
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235244"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>Nahraďte metodu v adresách URL OData je ve výchozím nastavení zakázána.

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.5, nahraďte metodu v adresách URL OData je standardně zakázáno. Pokud nahradit OData je zakázáno (nyní ve výchozím nastavení), veškeré žádosti uživatelů, včetně funkcí nahradit, (které neobvyklé) se nezdaří.|
|Doporučení|Pokud je potřeba nahradit – metoda (což je běžné), může být znovu zapnout pomocí nastavení konfigurace (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>). Metodu povoleno nahradit však můžete otevřít bezpečnostní zranitelná místa a by měla sloužit pouze po pečlivou revizi.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
