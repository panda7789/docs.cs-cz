---
ms.openlocfilehash: d3d336b9626437d8fb597de421005763afd5f021
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859368"
---
### <a name="changes-in-path-normalization"></a>Změny v cestě normalizace

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikací využívajících rozhraní .NET Framework 4.6.2, způsob, ve kterém modul runtime normalizuje cesty se změnil. Normalizace cestu zahrnuje upravuje řetězec, který identifikuje cestu nebo soubor, který vyhovuje na platnou cestu na cílovém operačním systému. Normalizace obvykle zahrnuje:<ul><li>Kanonizace oddělovače komponentu a adresáře.</li><li>Použití aktuální adresář pro relativní cestu.</li><li>Hodnocení relativní adresář (.) nebo nadřazený adresář (.) v cestě.</li><li>Oříznutí zadané znaky.</li></ul>Počínaje aplikací využívajících rozhraní .NET Framework 4.6.2, jsou ve výchozím nastavení povolené následující změny v normalizace cesta:<ul><li>Modul runtime odloží do operačního systému [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) funkce normalizace cesty.</li><li>Normalizace už zahrnuje ořezávání konec segmenty adresáře (například mezeru na konci názvu adresáře).</li><li>Podpora pro zařízení syntaxe cesty v režimu plné důvěryhodnosti, včetně <code>\\.\</code> and, for file I/O APIs in mscorlib.dll, <code>\\?\</code>.</li><li>The runtime does not validate device syntax paths.</li><li>The use of device syntax to access alternate data streams is supported.</li></ul>These changes improve performance while allowing methods to access previously inaccessible paths. Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.|
|Doporučení|Aplikace, které cílí .NET Framework 4.6.2 nebo novější můžete zrušit to změnit a použít starší verzi normalizace přidáním následujícího <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikace, které cílí na rozhraní .NET Framework 4.6.1 nebo starší ale jsou spuštěny v rozhraní .NET Framework 4.6.2 nebo novější můžete povolit změny normalizace cestu tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> .configuration souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Vedlejší|
|Version|4.6.2|
|type|Změna cílení|

