---
ms.openlocfilehash: 994876457f9745de99be30e567f400f69a0192fa
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70259783"
---
### <a name="changes-in-path-normalization"></a>Změny normalizace cesty

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, způsob, jakým se změnily cesty modulu runtime normalizovat. Normalizace cesty zahrnuje úpravu řetězce, který identifikuje cestu nebo soubor tak, aby splňoval platnou cestu v cílovém operačním systému. Normalizace obvykle zahrnuje:<ul><li>Kanonizace součásti a oddělovače adresářů.</li><li>Použití aktuálního adresáře na relativní cestu.</li><li>Vyhodnocuje se relativní adresář (.) nebo nadřazený adresář (..) v cestě.</li><li>Ořezávání zadaných znaků.</li></ul>Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, jsou ve výchozím nastavení povolené následující změny normalizace cesty:<ul><li>Modul runtime se odkládá na funkci [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) operačního systému k normalizaci cest.</li><li>Normalizace už nezahrnuje oříznutí konce segmentů adresáře (například místa na konci názvu adresáře).</li><li>Podpora syntaxe cesty zařízení v úplném vztahu důvěryhodnosti, `\\.\` včetně a, pro vstupně-výstupní rozhraní API souborů v knihovně Mscorlib `\\?\`. dll.</li><li>Modul runtime neověřuje cestu k syntaxi zařízení.</li><li>Podporuje se použití syntaxe zařízení pro přístup k alternativním datovým proudům.</li></ul>Tyto změny zlepšují výkon a zároveň umožňují přístup k dříve nepřístupným cestám metod. Aplikace, které cílí na .NET Framework 4.6.1 a starší verze, ale jsou spuštěné v .NET Framework 4.6.2 nebo novějším, tato změna neovlivní.|
|Doporučení|Aplikace, které cílí na .NET Framework 4.6.2 nebo novější, si mohou tuto změnu odhlásit a použít starší normalizaci přidáním následujícího do <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikace, které cílí na .NET Framework 4.6.1 nebo starší, ale běží na .NET Framework 4.6.2 nebo novějším, můžou povolit normalizaci cest přidáním následujícího řádku do <code>&lt;runtime&gt;</code> oddílu souboru Application. Configuration:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Vedlejší|
|Version|4.6.2|
|type|Změna cílení|
