---
ms.openlocfilehash: 6dc3669433804a4524c18d5a932f9879343ab508
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803644"
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
