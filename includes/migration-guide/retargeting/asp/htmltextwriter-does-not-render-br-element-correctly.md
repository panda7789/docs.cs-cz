---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804494"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="5741a-101">HtmlTextWriter nevykresluje `<br/>` prvek správně</span><span class="sxs-lookup"><span data-stu-id="5741a-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5741a-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5741a-102">Details</span></span>|<span data-ttu-id="5741a-103">Počínaje rozhraním .NET Framework 4.6, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> volání a <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> s elementem <code>&lt;BR /&gt;</code> správně vloží pouze jeden <code>&lt;BR /&gt;</code> (namísto dvou)</span><span class="sxs-lookup"><span data-stu-id="5741a-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="5741a-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="5741a-104">Suggestion</span></span>|<span data-ttu-id="5741a-105">Pokud aplikace závisela na <code>&lt;BR /&gt;</code> další <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> značce, měla by být volána podruhé.</span><span class="sxs-lookup"><span data-stu-id="5741a-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="5741a-106">Všimněte si, že tato změna chování ovlivňuje pouze aplikace, které cílí na rozhraní .NET Framework 4.6 nebo novější, takže další možností je cílit na předchozí verzi rozhraní .NET Framework, aby bylo možné získat staré chování.</span><span class="sxs-lookup"><span data-stu-id="5741a-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="5741a-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="5741a-107">Scope</span></span>|<span data-ttu-id="5741a-108">Edge</span><span class="sxs-lookup"><span data-stu-id="5741a-108">Edge</span></span>|
|<span data-ttu-id="5741a-109">Version</span><span class="sxs-lookup"><span data-stu-id="5741a-109">Version</span></span>|<span data-ttu-id="5741a-110">4.6</span><span class="sxs-lookup"><span data-stu-id="5741a-110">4.6</span></span>|
|<span data-ttu-id="5741a-111">Typ</span><span class="sxs-lookup"><span data-stu-id="5741a-111">Type</span></span>|<span data-ttu-id="5741a-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="5741a-112">Retargeting</span></span>|
|<span data-ttu-id="5741a-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5741a-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
