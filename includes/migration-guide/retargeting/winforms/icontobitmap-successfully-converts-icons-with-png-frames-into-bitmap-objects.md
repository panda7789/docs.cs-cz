---
ms.openlocfilehash: f4a5911787fa5f72be1dcd15c67b3f132c3f1110
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804406"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon.ToBitmap úspěšně převede ikony s rámečky PNG na objekty Bitmap

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikacemi, které cílí na rozhraní <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> .NET Framework 4.6, metoda úspěšně převede ikony s rámečky PNG na objekty Bitmap.<p/>V aplikacích, které cílí na rozhraní .NET Framework <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 4.5.2 a starší verze, metoda vyvolá výjimku, <xref:System.ArgumentOutOfRangeException> pokud icon objekt má png rámce.<p/>Tato změna má vliv na aplikace, které jsou překompilovány tak, <xref:System.ArgumentOutOfRangeException> aby cílili na rozhraní .NET Framework 4.6 a které implementují speciální zpracování pro objekt, který je vyvolán, když má objekt PNG rámce PNG. Při spuštění v rámci rozhraní .NET Framework 4.6 je převod úspěšný, <xref:System.ArgumentOutOfRangeException> již není vyvolána a proto obslužná rutina výjimky již není vyvolána.|
|Návrh|Pokud je toto chování nežádoucí, můžete zachovat předchozí chování <code>&lt;runtime&gt;</code> přidáním následujícího prvku do části souboru app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>Pokud soubor app.config již <code>AppContextSwitchOverrides</code> prvek obsahuje, měla by být nová hodnota sloučena s atributem hodnoty, jako je tento:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|
