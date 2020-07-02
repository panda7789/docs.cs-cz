---
ms.openlocfilehash: 8f03e5166e7f1f598e9bba7fb8c550809f287b82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615633"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter nevykresluje `<br/>` element správně

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,6, volání <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> a <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> s `<BR />` elementem budou správně vložena pouze jedna `<BR />` (místo dvou).

#### <a name="suggestion"></a>Návrh

Pokud je aplikace závislá na `<BR />` značce navíc, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> měla by být volána podruhé. Všimněte si, že tato změna chování ovlivňuje pouze aplikace, které cílí na .NET Framework 4,6 nebo novější, takže další možnost je cílit na předchozí verzi .NET Framework, aby bylo možné získat staré chování.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType>
- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType>
