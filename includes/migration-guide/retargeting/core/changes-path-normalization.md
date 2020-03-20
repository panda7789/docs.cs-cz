---
ms.openlocfilehash: 994876457f9745de99be30e567f400f69a0192fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70259783"
---
### <a name="changes-in-path-normalization"></a>Změny normalizace cesty

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.2, změnil se způsob, jakým běhnormalizuje cesty. Normalizace cesty zahrnuje úpravu řetězce, který identifikuje cestu nebo soubor tak, aby odpovídalplatné cestě v cílovém operačním systému. Normalizace obvykle zahrnuje:<ul><li>Oddělovače komponent a adresářů canonicalizing.</li><li>Použití aktuálního adresáře na relativní cestu.</li><li>Vyhodnocení relativního adresáře (.) nebo nadřazeného adresáře (..) v cestě.</li><li>Oříznutí určených znaků.</li></ul>Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.2, jsou ve výchozím nastavení povoleny následující změny normalizace cesty:<ul><li>Runtime odkládá na funkci [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) operačního systému normalizovat cesty.</li><li>Normalizace již nezahrnuje oříznutí konce segmentů adresáře (například mezeru na konci názvu adresáře).</li><li>Podpora syntaxe cesty zařízení v `\\.\` plném vztahu důvěryhodnosti, včetně rozhraní API vstupně-nosných souborů v souboru mscorlib.dll . `\\?\`</li><li>Runtime neověřuje cesty syntaxe zařízení.</li><li>Je podporováno použití syntaxe zařízení pro přístup k alternativním datovým proudům.</li></ul>Tyto změny zlepšují výkon a zároveň umožňují metodám přístup k dříve nepřístupným cestám. Aplikace, které cílí na rozhraní .NET Framework 4.6.1 a starší verze, ale jsou spuštěny v rámci rozhraní .NET Framework 4.6.2 nebo novější, nejsou touto změnou ovlivněny.|
|Návrh|Aplikace, které cílí na rozhraní .NET Framework 4.6.2 nebo novější, se mohou <code>&lt;runtime&gt;</code> odhlásit z této změny a používat starší normalizaci přidáním následujícího textu do části konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikace, které cílí na rozhraní .NET Framework 4.6.1 nebo starší, ale jsou spuštěny v rozhraní .NET Framework <code>&lt;runtime&gt;</code> 4.6.2 nebo novějším, mohou povolit změny normalizace cesty přidáním následujícího řádku do části souboru konfigurace aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Změna cílení|
