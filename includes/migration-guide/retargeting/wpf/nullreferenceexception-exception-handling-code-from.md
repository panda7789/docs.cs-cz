---
ms.openlocfilehash: 824d75585efd40937c1a48376ec7862cba1a8fa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235496"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException v kódu zpracování výjimky z ImageSourceConverter.ConvertFrom

|   |   |
|---|---|
|Podrobnosti|Chyba v kódu zpracování <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> výjimky <xref:System.NullReferenceException?displayProperty=name> pro způsobil nesprávné vyvolat místo <xref:System.IO.DirectoryNotFoundException?displayProperty=name> zamýšlené <xref:System.IO.FileNotFoundException?displayProperty=name>výjimky ( nebo ). Tato změna opravuje tuto chybu tak, aby metoda nyní vyvolá správnou výjimku. <p/>Ve výchozím nastavení všechny aplikace cílení .NET Framework 4.6.2 a starší nadále vyvolat <xref:System.NullReferenceException?displayProperty=name> kompatibilitu. Vývojáři cílení .NET Framework 4.7 a vyšší by měl vidět správné výjimky.|
|Návrh|Vývojáři, kteří se <xref:System.NullReferenceException?displayProperty=name> chtějí vrátit k získání při cílení na rozhraní .NET Framework 4.7 nebo novější, mohou přidat nebo sloučit následující do souboru App.config své aplikace:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|
