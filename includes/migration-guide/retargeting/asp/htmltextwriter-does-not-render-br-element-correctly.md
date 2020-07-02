---
ms.openlocfilehash: 8f03e5166e7f1f598e9bba7fb8c550809f287b82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615633"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="7592c-101">HtmlTextWriter nevykresluje `<br/>` element správně</span><span class="sxs-lookup"><span data-stu-id="7592c-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

#### <a name="details"></a><span data-ttu-id="7592c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7592c-102">Details</span></span>

<span data-ttu-id="7592c-103">Počínaje .NET Framework 4,6, volání <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> a <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> s `<BR />` elementem budou správně vložena pouze jedna `<BR />` (místo dvou).</span><span class="sxs-lookup"><span data-stu-id="7592c-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a `<BR />` element will correctly insert only one `<BR />` (instead of two)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7592c-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="7592c-104">Suggestion</span></span>

<span data-ttu-id="7592c-105">Pokud je aplikace závislá na `<BR />` značce navíc, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> měla by být volána podruhé.</span><span class="sxs-lookup"><span data-stu-id="7592c-105">If an app depended on the extra `<BR />` tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="7592c-106">Všimněte si, že tato změna chování ovlivňuje pouze aplikace, které cílí na .NET Framework 4,6 nebo novější, takže další možnost je cílit na předchozí verzi .NET Framework, aby bylo možné získat staré chování.</span><span class="sxs-lookup"><span data-stu-id="7592c-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>

| <span data-ttu-id="7592c-107">Name</span><span class="sxs-lookup"><span data-stu-id="7592c-107">Name</span></span>    | <span data-ttu-id="7592c-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7592c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7592c-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="7592c-109">Scope</span></span>   | <span data-ttu-id="7592c-110">Edge</span><span class="sxs-lookup"><span data-stu-id="7592c-110">Edge</span></span>        |
| <span data-ttu-id="7592c-111">Verze</span><span class="sxs-lookup"><span data-stu-id="7592c-111">Version</span></span> | <span data-ttu-id="7592c-112">4.6</span><span class="sxs-lookup"><span data-stu-id="7592c-112">4.6</span></span>         |
| <span data-ttu-id="7592c-113">Typ</span><span class="sxs-lookup"><span data-stu-id="7592c-113">Type</span></span>    | <span data-ttu-id="7592c-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="7592c-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="7592c-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7592c-115">Affected APIs</span></span>

- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType>
- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType>
