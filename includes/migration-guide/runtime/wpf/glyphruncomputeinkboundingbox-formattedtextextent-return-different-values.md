---
ms.openlocfilehash: 00ffc782c9a15c0d88f797f52372b4658706b350
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620085"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a><span data-ttu-id="f653a-101">GlyphRun. ComputeInkBoundingBox () a FormattedText. Rozsah vrací jiné hodnoty počínaje .NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="f653a-101">GlyphRun.ComputeInkBoundingBox() and FormattedText.Extent return different values beginning in .NET Framework 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="f653a-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f653a-102">Details</span></span>

<span data-ttu-id="f653a-103">Bylo provedeno vylepšení <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> a <xref:System.Windows.Media.FormattedText.Extent> v .NET Framework 4,5, které řeší problémy, kde jsou pole příliš malá pro obsažené glyfy v některých případech v .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="f653a-103">Improvements were made to <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> and <xref:System.Windows.Media.FormattedText.Extent> in the .NET Framework 4.5 to address issues where the boxes were too small for the contained glyphs in some cases in the .NET Framework 4.0.</span></span> <span data-ttu-id="f653a-104">V důsledku toho budou některé ohraničovací rámečky větší počínaje .NET Framework 4,5, což vede k drobným rozdílům v rozložení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f653a-104">As a result of this, some bounding boxes will be larger beginning in the .NET Framework 4.5, resulting in subtle differences in UI layout.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f653a-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="f653a-105">Suggestion</span></span>

<span data-ttu-id="f653a-106">Počítejte s tím, že se zvýšily některé velikosti ohraničovacích rámečků glyfů.</span><span class="sxs-lookup"><span data-stu-id="f653a-106">Be aware that some glyph bounding box sizes have increased.</span></span> <span data-ttu-id="f653a-107">Tyto změny obvykle vylepšit testování v případě prezentace a v krabici, ale pokud je žádoucí chování starší (pre-.NET 4,5), může být do souboru app.config přizpůsobeno přidáním následujícího záznamu:</span><span class="sxs-lookup"><span data-stu-id="f653a-107">These changes will usually improve presentation and hit box testing, but if the older (pre-.NET 4.5) behavior is desired, it can be opted into by adding the following entry to the app.config file:</span></span><pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="f653a-108">Name</span><span class="sxs-lookup"><span data-stu-id="f653a-108">Name</span></span>    | <span data-ttu-id="f653a-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f653a-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f653a-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="f653a-110">Scope</span></span>   |<span data-ttu-id="f653a-111">Edge</span><span class="sxs-lookup"><span data-stu-id="f653a-111">Edge</span></span>|
|<span data-ttu-id="f653a-112">Verze</span><span class="sxs-lookup"><span data-stu-id="f653a-112">Version</span></span>|<span data-ttu-id="f653a-113">4.5</span><span class="sxs-lookup"><span data-stu-id="f653a-113">4.5</span></span>|
|<span data-ttu-id="f653a-114">Typ</span><span class="sxs-lookup"><span data-stu-id="f653a-114">Type</span></span>|<span data-ttu-id="f653a-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="f653a-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f653a-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f653a-116">Affected APIs</span></span>

-<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|
