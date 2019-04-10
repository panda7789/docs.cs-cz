---
ms.openlocfilehash: c9c46793a0f66894649796d960547848ff5ebf8c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235214"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>Prvků GridViews s AllowCustomPaging na hodnotu nastavenou na hodnotu true může vyvolat události PageIndexChanging při opuštění poslední stránky zobrazení

|   |   |
|---|---|
|Podrobnosti|Způsobí chybu v rozhraní .NET Framework 4.5 <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> k někdy neaktivuje pro <xref:System.Web.UI.WebControls.GridView?displayProperty=name>, které jste povolili <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name>.|
|Doporučení|Tento problém jsme opravili v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework. Jako alternativní, můžete aplikaci provést explicitní BindGrid na žádném <code>Page_Load</code> narazí, který tyto podmínky ( <xref:System.Web.UI.WebControls.GridView?displayProperty=name> je na poslední stránce a poslední<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> se liší od <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>). Aplikaci můžete také upravit tak, aby povolit stránkování (namísto vlastní stránkování), jak tento scénář neukazuje problém.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
