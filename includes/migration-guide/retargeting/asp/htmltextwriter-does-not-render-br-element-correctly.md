---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088460"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="28599-101">HtmlTextWriter nevykresluje `<br/>` element správně</span><span class="sxs-lookup"><span data-stu-id="28599-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="28599-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="28599-102">Details</span></span>|<span data-ttu-id="28599-103">Počínaje .NET Framework 4.6, volání <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> a <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> s <code>&lt;BR /&gt;</code> prvek se vloží správně pouze jeden <code>&lt;BR /&gt;</code> (místo dvou)</span><span class="sxs-lookup"><span data-stu-id="28599-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="28599-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="28599-104">Suggestion</span></span>|<span data-ttu-id="28599-105">Pokud aplikace závisí na nadbytečné <code>&lt;BR /&gt;</code> značky, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> by měla být volána podruhé.</span><span class="sxs-lookup"><span data-stu-id="28599-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="28599-106">Všimněte si, že tato změna chování ovlivní pouze aplikace, které cílí rozhraní .NET Framework 4.6 nebo novější, takže další možnost je k cílení na předchozí verzi rozhraní .NET Framework zajistí staré chování.</span><span class="sxs-lookup"><span data-stu-id="28599-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="28599-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="28599-107">Scope</span></span>|<span data-ttu-id="28599-108">Edge</span><span class="sxs-lookup"><span data-stu-id="28599-108">Edge</span></span>|
|<span data-ttu-id="28599-109">Version</span><span class="sxs-lookup"><span data-stu-id="28599-109">Version</span></span>|<span data-ttu-id="28599-110">4.6</span><span class="sxs-lookup"><span data-stu-id="28599-110">4.6</span></span>|
|<span data-ttu-id="28599-111">Type</span><span class="sxs-lookup"><span data-stu-id="28599-111">Type</span></span>|<span data-ttu-id="28599-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="28599-112">Retargeting</span></span>|
|<span data-ttu-id="28599-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="28599-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
