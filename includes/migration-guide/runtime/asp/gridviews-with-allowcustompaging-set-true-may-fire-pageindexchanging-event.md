---
ms.openlocfilehash: 3b329bf5ba2af4d3ab9c3e203e99daba8ca0d0c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619921"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>GridViews s AllowCustomPaging na nastavenou na hodnotu true může vyvolat událost PageIndexChanging při ponechávání poslední stránky zobrazení.

#### <a name="details"></a>Podrobnosti

Chyba v .NET Framework 4,5 způsobí <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> , že se někdy neaktivují pro <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> s, které jsou povolené <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName> .

#### <a name="suggestion"></a>Návrh

Tento problém byl opravený v .NET Framework 4,6 a může se řešit upgradem na verzi .NET Framework. V rámci práce v aplikaci může aplikace provádět explicitní BindGrid <code>Page_Load</code> , ve které by se tyto podmínky mohly <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> vymezit (je na poslední stránce a poslední <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> se liší od <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> ). Alternativně lze aplikaci upravit tak, aby povolovala stránkování (místo vlastního stránkování), protože tento scénář problém předvádí.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
