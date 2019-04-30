---
ms.openlocfilehash: d57cd5a9d41a7d2d93f03216d534f14831bcefe0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758338"
---
### <a name="changes-in-path-normalization"></a>Změny v cestě normalizace

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikací využívajících rozhraní .NET Framework 4.6.2, způsob, ve kterém modul runtime normalizuje cesty se změnil. Normalizace cestu zahrnuje upravuje řetězec, který identifikuje cestu nebo soubor, který vyhovuje na platnou cestu na cílovém operačním systému. Normalizace obvykle zahrnuje:<ul><li>Kanonizace oddělovače komponentu a adresáře.</li><li>Použití aktuální adresář pro relativní cestu.</li><li>Hodnocení relativní adresář (.) nebo nadřazený adresář (.) v cestě.</li><li>Oříznutí zadané znaky.</li></ul>Počínaje aplikací využívajících rozhraní .NET Framework 4.6.2, jsou ve výchozím nastavení povolené následující změny v normalizace cesta:<ul><li>Modul runtime odloží do operačního systému [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) funkce normalizace cesty.</li><li>Normalizace už zahrnuje ořezávání konec segmenty adresáře (například mezeru na konci názvu adresáře).</li><li>Podpora pro zařízení syntaxe cesty v režimu plné důvěryhodnosti, včetně `\\.\` a pro rozhraní API vstupně-výstupní operace souboru v mscorlib.dll, `\\?\`.</li><li>Modul runtime nelze ověřit zařízení syntaxe cesty.</li><li>Použití syntaxe zařízení pro přístup k alternativní datové proudy je podporované.</li></ul>Tyto změny zlepšit výkon při povolení metody pro přístup k dříve nedostupných cesty. Aplikace, které cílí na rozhraní .NET Framework 4.6.1 a starší verze, ale jsou spuštěny v rozhraní .NET Framework 4.6.2 nebo novější se tato změna nemá vliv.|
|Doporučení|Aplikace, které cílí .NET Framework 4.6.2 nebo novější můžete zrušit to změnit a použít starší verzi normalizace přidáním následujícího <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikace, které cílí na rozhraní .NET Framework 4.6.1 nebo starší ale jsou spuštěny v rozhraní .NET Framework 4.6.2 nebo novější můžete povolit změny normalizace cestu tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> .configuration souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Type|Změna cílení|
