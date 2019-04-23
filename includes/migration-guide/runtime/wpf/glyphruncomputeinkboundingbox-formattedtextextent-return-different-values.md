---
ms.openlocfilehash: 059aa6f5885634b22b64d594563973f17fd2c4e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803645"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a>GlyphRun.ComputeInkBoundingBox() a FormattedText.Extent vracet různé hodnoty od v rozhraní .NET Framework 4.5

|   |   |
|---|---|
|Podrobnosti|Byly vylepšeny <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> a <xref:System.Windows.Media.FormattedText.Extent> v rozhraní .NET Framework 4.5 pro řešení potíží s, ve kterém byly do polí příliš malá pro obsaženého glyphs v některých případech v rozhraní .NET Framework 4.0. V důsledku toho budou některé ohraničující polí větší od verze rozhraní .NET Framework 4.5, což vede k drobné rozdíly v rozložení uživatelského rozhraní.|
|Doporučení|Mějte na paměti, že máte vyšší ohraničující velikostech polí některé glyfy. Tyto změny obvykle zlepší prezentace a testování přístupů pole, ale pokud se požaduje starší chování (předběžné .NET 4.5), ho můžete vyjádřit výslovný souhlas do tak, že přidáte následující položku do souboru app.config:<pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|
