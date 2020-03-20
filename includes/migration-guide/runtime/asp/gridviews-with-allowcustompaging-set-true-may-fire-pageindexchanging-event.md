---
ms.openlocfilehash: c9c46793a0f66894649796d960547848ff5ebf8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858525"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>GridViews s AllowCustomPaging nastavena na hodnotu true může požár PageIndexChanging událost při opuštění poslední stránku zobrazení

|   |   |
|---|---|
|Podrobnosti|Chyba v rozhraní .NET Framework <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> 4.5 způsobí, že někdy není oheň pro <xref:System.Web.UI.WebControls.GridView?displayProperty=name>s, které mají povoleno <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name>.|
|Návrh|Tento problém byl vyřešen v rozhraní .NET Framework 4.6 a může být vyřešen upgradem na tuto verzi rozhraní .NET Framework. Jako řešení, aplikace může provést explicitní BindGrid <code>Page_Load</code> na všechny, které <xref:System.Web.UI.WebControls.GridView?displayProperty=name> by zasáhly tyto<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> podmínky (je na poslední stránce a Poslední se liší od <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>). Alternativně aplikace může být upravena tak, aby povolit stránkování (namísto vlastní stránkování), jako tento scénář neukazuje problém.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
