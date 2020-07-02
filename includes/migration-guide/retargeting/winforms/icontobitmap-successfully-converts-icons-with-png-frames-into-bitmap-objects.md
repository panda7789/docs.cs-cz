---
ms.openlocfilehash: 811b1a91169eeebfa056d9ecdb07d342d3b32d85
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615717"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon. ToBitmap úspěšně převádí ikony s snímky PNG na bitmapové objekty.

#### <a name="details"></a>Podrobnosti

Počínaje aplikacemi, které cílí na .NET Framework 4,6, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> Metoda úspěšně převede ikony s snímky PNG na bitmapové objekty.<p/>V aplikacích, které cílí na .NET Framework 4.5.2 a starší verze, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> vyvolá metoda <xref:System.ArgumentOutOfRangeException> výjimku, pokud objekt Icon obsahuje snímky PNG.<p/>Tato změna ovlivní aplikace, které jsou znovu zkompilovány pro cílení na .NET Framework 4,6 a které implementují speciální zpracování pro <xref:System.ArgumentOutOfRangeException> výjimku, která je vyvolána, když objekt Icon má snímky PNG. Při spuštění pod .NET Framework 4,6 je převod úspěšný, <xref:System.ArgumentOutOfRangeException> již není vyvolán, a proto obslužná rutina výjimky již není vyvolána.

#### <a name="suggestion"></a>Návrh

Pokud je toto chování nežádoucí, můžete předchozí chování zachovat přidáním následujícího elementu do `<runtime>` části souboru app.config:

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>

Pokud app.config soubor již obsahuje `AppContextSwitchOverrides` element, nová hodnota by měla být sloučena s atributem value takto:

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType>
