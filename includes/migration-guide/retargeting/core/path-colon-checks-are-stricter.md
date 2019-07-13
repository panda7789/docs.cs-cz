---
ms.openlocfilehash: 7f551fbc194d2da2fdae6bcc7025c20b03aadda2
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859284"
---
### <a name="path-colon-checks-are-stricter"></a>Byly přísnější kontroly dvojtečka cesta

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 počet změn nebyly zadány podporují dříve nepodporované cesty (jak formát a). Kontroly syntaxe správná jednotka oddělovač (dvojtečka) byly provedeny více správné, který má vedlejší účinek blokování některé cesty identifikátoru URI v několika vyberte rozhraní API cesta kde používají tolerovat.|
|Doporučení|Pokud předávání identifikátorů URI pro ovlivněné rozhraní API, upravte řetězec, který má být nejprve právní cesta.<ul><li>Schéma ručně odebrat z adres URL (třeba odebrat <code>file://</code> z adresy URL)</li><li>Předat identifikátor URI <xref:System.Uri> třídy a použití <xref:System.Uri.LocalPath></li></ul>Alternativně můžete zrušit nové normalizace cestu tak, že nastavíte <code>Switch.System.IO.UseLegacyPathHandling</code> přepínač AppContext na hodnotu true.|
|Scope|Edge|
|Version|4.6.2|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|

