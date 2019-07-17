---
ms.openlocfilehash: 824d75585efd40937c1a48376ec7862cba1a8fa3
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235496"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException v kódu z ImageSourceConverter.ConvertFrom pro zpracování výjimek

|   |   |
|---|---|
|Podrobnosti|Chyba v kód pro zpracování výjimek <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> způsobit nesprávné <xref:System.NullReferenceException?displayProperty=name> vyvolání namísto zamýšlené výjimky ( <xref:System.IO.DirectoryNotFoundException?displayProperty=name> nebo <xref:System.IO.FileNotFoundException?displayProperty=name>). Tato změna řeší tuto chybu tak, aby metoda vyvolá nyní správná výjimka. <p/>Tím, že výchozí všechny aplikace, které cílí na rozhraní .NET Framework 4.6.2 a starší i nadále throw <xref:System.NullReferenceException?displayProperty=name> z důvodu kompatibility. Vývojáři cílí na .NET Framework 4.7 výše by se zobrazit správné výjimky.|
|Doporučení|Vývojáři, kteří chtějí vrátit k získání <xref:System.NullReferenceException?displayProperty=name> při cílení na rozhraní .NET Framework 4.7 nebo novější můžete přidat/merge následujícího souboru App.config jejich aplikace:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Scope|Edge|
|Version|4.7|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|
