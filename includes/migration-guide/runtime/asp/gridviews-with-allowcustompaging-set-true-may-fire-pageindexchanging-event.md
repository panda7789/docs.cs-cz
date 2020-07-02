---
ms.openlocfilehash: 3b329bf5ba2af4d3ab9c3e203e99daba8ca0d0c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619921"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a><span data-ttu-id="e6cf5-101">GridViews s AllowCustomPaging na nastavenou na hodnotu true může vyvolat událost PageIndexChanging při ponechávání poslední stránky zobrazení.</span><span class="sxs-lookup"><span data-stu-id="e6cf5-101">GridViews with AllowCustomPaging set to true may fire the PageIndexChanging event when leaving the final page of the view</span></span>

#### <a name="details"></a><span data-ttu-id="e6cf5-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e6cf5-102">Details</span></span>

<span data-ttu-id="e6cf5-103">Chyba v .NET Framework 4,5 způsobí <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> , že se někdy neaktivují pro <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> s, které jsou povolené <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="e6cf5-103">A bug in the .NET Framework 4.5 causes <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> to sometimes not fire for <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName>s that have enabled <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e6cf5-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="e6cf5-104">Suggestion</span></span>

<span data-ttu-id="e6cf5-105">Tento problém byl opravený v .NET Framework 4,6 a může se řešit upgradem na verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e6cf5-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span> <span data-ttu-id="e6cf5-106">V rámci práce v aplikaci může aplikace provádět explicitní BindGrid <code>Page_Load</code> , ve které by se tyto podmínky mohly <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> vymezit (je na poslední stránce a poslední <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> se liší od <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="e6cf5-106">As a work-around, the app can do an explicit BindGrid on any <code>Page_Load</code> that would hit these conditions (the <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> is on the last page and Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> is different from <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>).</span></span> <span data-ttu-id="e6cf5-107">Alternativně lze aplikaci upravit tak, aby povolovala stránkování (místo vlastního stránkování), protože tento scénář problém předvádí.</span><span class="sxs-lookup"><span data-stu-id="e6cf5-107">Alternatively, the app can be modified to allow paging (instead of custom paging), as that scenario does not demonstrate the problem.</span></span>

| <span data-ttu-id="e6cf5-108">Name</span><span class="sxs-lookup"><span data-stu-id="e6cf5-108">Name</span></span>    | <span data-ttu-id="e6cf5-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e6cf5-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e6cf5-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e6cf5-110">Scope</span></span>   |<span data-ttu-id="e6cf5-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="e6cf5-111">Minor</span></span>|
|<span data-ttu-id="e6cf5-112">Verze</span><span class="sxs-lookup"><span data-stu-id="e6cf5-112">Version</span></span>|<span data-ttu-id="e6cf5-113">4.5</span><span class="sxs-lookup"><span data-stu-id="e6cf5-113">4.5</span></span>|
|<span data-ttu-id="e6cf5-114">Typ</span><span class="sxs-lookup"><span data-stu-id="e6cf5-114">Type</span></span>|<span data-ttu-id="e6cf5-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="e6cf5-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e6cf5-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e6cf5-116">Affected APIs</span></span>

-<xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
