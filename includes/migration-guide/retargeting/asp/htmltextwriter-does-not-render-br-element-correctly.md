---
ms.openlocfilehash: 0ab6be6f2c6d8ebbe67051e4e3f967a325e654c8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804494"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="09593-101">HtmlTextWriter nevykresluje `<br/>` element správně</span><span class="sxs-lookup"><span data-stu-id="09593-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="09593-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="09593-102">Details</span></span>|<span data-ttu-id="09593-103">Počínaje .NET Framework 4.6, volání <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> a <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> s <code>&lt;BR /&gt;</code> prvek se vloží správně pouze jeden <code>&lt;BR /&gt;</code> (místo dvou)</span><span class="sxs-lookup"><span data-stu-id="09593-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="09593-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="09593-104">Suggestion</span></span>|<span data-ttu-id="09593-105">Pokud aplikace závisí na nadbytečné <code>&lt;BR /&gt;</code> značky, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> by měla být volána podruhé.</span><span class="sxs-lookup"><span data-stu-id="09593-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="09593-106">Všimněte si, že tato změna chování ovlivní pouze aplikace, které cílí rozhraní .NET Framework 4.6 nebo novější, takže další možnost je k cílení na předchozí verzi rozhraní .NET Framework zajistí staré chování.</span><span class="sxs-lookup"><span data-stu-id="09593-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="09593-107">Scope</span><span class="sxs-lookup"><span data-stu-id="09593-107">Scope</span></span>|<span data-ttu-id="09593-108">Edge</span><span class="sxs-lookup"><span data-stu-id="09593-108">Edge</span></span>|
|<span data-ttu-id="09593-109">Version</span><span class="sxs-lookup"><span data-stu-id="09593-109">Version</span></span>|<span data-ttu-id="09593-110">4.6</span><span class="sxs-lookup"><span data-stu-id="09593-110">4.6</span></span>|
|<span data-ttu-id="09593-111">type</span><span class="sxs-lookup"><span data-stu-id="09593-111">Type</span></span>|<span data-ttu-id="09593-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="09593-112">Retargeting</span></span>|
|<span data-ttu-id="09593-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="09593-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|

