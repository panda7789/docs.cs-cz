---
ms.openlocfilehash: a51738fa75ba2dd4574549fce2570df8231c4cae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234895"
---
### <a name="path-colon-checks-are-stricter"></a>Byly přísnější kontroly dvojtečka cesta

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 počet změn nebyly zadány podporují dříve nepodporované cesty (jak formát a). Kontroly syntaxe správná jednotka oddělovač (dvojtečka) byly provedeny více správné, který má vedlejší účinek blokování některé cesty identifikátoru URI v několika vyberte rozhraní API cesta kde používají tolerovat.|
|Doporučení|Pokud předávání identifikátorů URI pro ovlivněné rozhraní API, upravte řetězec, který má být nejprve právní cesta.<ul><li>Schéma ručně odebrat z adres URL (třeba odebrat <code>file://</code> z adresy URL)</li><li>Předat identifikátor URI <xref:System.Uri> třídy a použití <xref:System.Uri.LocalPath></li></ul>Alternativně můžete zrušit nové normalizace cestu tak, že nastavíte <code>Switch.System.IO.UseLegacyPathHandling</code> přepínač AppContext na hodnotu true.|
|Rozsah|Edge|
|Version|4.6.2|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|
