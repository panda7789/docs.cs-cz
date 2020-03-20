---
ms.openlocfilehash: a51738fa75ba2dd4574549fce2570df8231c4cae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859284"
---
### <a name="path-colon-checks-are-stricter"></a>Kontroly dvojtečky cesty jsou přísnější

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 byla provedena řada změn pro podporu dříve nepodporovaných cest (v délce i formátu). Kontroly správné syntaxe oddělovače jednotek (dvojtečka) byly provedeny více správné, což mělo vedlejší účinek blokování některých cest URI v několika vybraných rozhraní chodišti rozhraní API, kde byly tolerovány.|
|Návrh|Pokud předání identifikátoru URI ovlivněným souborům API upravte nejprve řetězec jako legální cestu.<ul><li>Ruční odebrání schématu z adres URL (např. odebrání <code>file://</code> z adres URL)</li><li>Předat identifikátor URI <xref:System.Uri> do třídy a použít<xref:System.Uri.LocalPath></li></ul>Případně můžete odhlásit z normalizace nové cesty <code>Switch.System.IO.UseLegacyPathHandling</code> nastavením AppContext přepínač true.|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|
