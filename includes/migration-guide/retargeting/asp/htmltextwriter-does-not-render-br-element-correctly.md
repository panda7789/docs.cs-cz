---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803718"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="0545f-101">HtmlTextWriter nevykresluje `<br/>` element správně</span><span class="sxs-lookup"><span data-stu-id="0545f-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0545f-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0545f-102">Details</span></span>|<span data-ttu-id="0545f-103">Počínaje .NET Framework 4.6, volání <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> a <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> s <code>&lt;BR /&gt;</code> prvek se vloží správně pouze jeden <code>&lt;BR /&gt;</code> (místo dvou)</span><span class="sxs-lookup"><span data-stu-id="0545f-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="0545f-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="0545f-104">Suggestion</span></span>|<span data-ttu-id="0545f-105">Pokud aplikace závisí na nadbytečné <code>&lt;BR /&gt;</code> značky, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> by měla být volána podruhé.</span><span class="sxs-lookup"><span data-stu-id="0545f-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="0545f-106">Všimněte si, že tato změna chování ovlivní pouze aplikace, které cílí rozhraní .NET Framework 4.6 nebo novější, takže další možnost je k cílení na předchozí verzi rozhraní .NET Framework zajistí staré chování.</span><span class="sxs-lookup"><span data-stu-id="0545f-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="0545f-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="0545f-107">Scope</span></span>|<span data-ttu-id="0545f-108">Edge</span><span class="sxs-lookup"><span data-stu-id="0545f-108">Edge</span></span>|
|<span data-ttu-id="0545f-109">Version</span><span class="sxs-lookup"><span data-stu-id="0545f-109">Version</span></span>|<span data-ttu-id="0545f-110">4.6</span><span class="sxs-lookup"><span data-stu-id="0545f-110">4.6</span></span>|
|<span data-ttu-id="0545f-111">Type</span><span class="sxs-lookup"><span data-stu-id="0545f-111">Type</span></span>|<span data-ttu-id="0545f-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="0545f-112">Retargeting</span></span>|
|<span data-ttu-id="0545f-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0545f-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
