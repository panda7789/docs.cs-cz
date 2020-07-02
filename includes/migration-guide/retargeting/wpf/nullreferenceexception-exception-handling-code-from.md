---
ms.openlocfilehash: 9c9c4ec55143ef991e9b69a389e0f3368263bb4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614555"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException v kódu pro zpracování výjimek z ImageSourceConverter. ConvertFrom

#### <a name="details"></a>Podrobnosti

Chyba v kódu zpracování výjimky pro <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> způsobila nesprávnou <xref:System.NullReferenceException?displayProperty=fullName> výjimku namísto zamýšlené výjimky ( <xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> nebo <xref:System.IO.FileNotFoundException?displayProperty=fullName> ). Tato změna opravuje tuto chybu tak, aby metoda nyní vyvolala správnou výjimku. <p/>Ve výchozím nastavení všechny aplikace cílené .NET Framework 4.6.2 a starší pokračují <xref:System.NullReferenceException?displayProperty=fullName> v vyvolání kompatibility. Vývojáři, kteří cílí na .NET Framework 4,7 a vyšší, by měli vidět správné výjimky.

#### <a name="suggestion"></a>Návrh

Vývojáři, kteří se chtějí vrátit k získání, <xref:System.NullReferenceException?displayProperty=fullName> když cílí na .NET Framework 4,7 nebo novější, můžou do souboru App.config aplikace přidat nebo sloučit následující:

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4,7         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType>
