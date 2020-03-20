---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804494"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter nevykresluje `<br/>` prvek správně

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.6, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> volání a <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> s elementem <code>&lt;BR /&gt;</code> správně vloží pouze jeden <code>&lt;BR /&gt;</code> (namísto dvou)|
|Návrh|Pokud aplikace závisela na <code>&lt;BR /&gt;</code> další <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> značce, měla by být volána podruhé. Všimněte si, že tato změna chování ovlivňuje pouze aplikace, které cílí na rozhraní .NET Framework 4.6 nebo novější, takže další možností je cílit na předchozí verzi rozhraní .NET Framework, aby bylo možné získat staré chování.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
