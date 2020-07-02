---
ms.openlocfilehash: b2fcacdb02c411c4dcb12051bf0c6759faccdea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620065"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>Metoda Replace v adresách URL OData je ve výchozím nastavení zakázaná.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,5 je metoda Replace v adresách URL OData ve výchozím nastavení zakázaná. Pokud je nahrazení OData zakázané (teď ve výchozím nastavení), všechny požadavky uživatelů, včetně funkcí nahrazení (které nejsou běžné), selžou.

#### <a name="suggestion"></a>Návrh

Pokud je vyžadována metoda Replace (která je neobvyklá), může být znovu povolena prostřednictvím nastavení konfigurace ( <xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName> ). Povolená metoda Replace ale může otevřít bezpečnostní ohrožení zabezpečení a měla by se používat jenom po pečlivém přezkoumání.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
