---
ms.openlocfilehash: 00ffc782c9a15c0d88f797f52372b4658706b350
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620085"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a>GlyphRun. ComputeInkBoundingBox () a FormattedText. Rozsah vrací jiné hodnoty počínaje .NET Framework 4,5

#### <a name="details"></a>Podrobnosti

Bylo provedeno vylepšení <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> a <xref:System.Windows.Media.FormattedText.Extent> v .NET Framework 4,5, které řeší problémy, kde jsou pole příliš malá pro obsažené glyfy v některých případech v .NET Framework 4,0. V důsledku toho budou některé ohraničovací rámečky větší počínaje .NET Framework 4,5, což vede k drobným rozdílům v rozložení uživatelského rozhraní.

#### <a name="suggestion"></a>Návrh

Počítejte s tím, že se zvýšily některé velikosti ohraničovacích rámečků glyfů. Tyto změny obvykle vylepšit testování v případě prezentace a v krabici, ale pokud je žádoucí chování starší (pre-.NET 4,5), může být do souboru app.config přizpůsobeno přidáním následujícího záznamu:<pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|
