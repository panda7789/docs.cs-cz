---
ms.openlocfilehash: ae557ce57557d027dba35b7da213c08aee85f2c7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621977"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a><span data-ttu-id="0a100-101">ASP.NET opravovat zpracování ovládacího prvku zaškrtávací políčko InputAttributes a LabelAttributes pro WebForms</span><span class="sxs-lookup"><span data-stu-id="0a100-101">ASP.NET Fix handling of InputAttributes and LabelAttributes for WebForms CheckBox control</span></span>

#### <a name="details"></a><span data-ttu-id="0a100-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0a100-102">Details</span></span>

<span data-ttu-id="0a100-103">Pro aplikace, které cílí na .NET Framework 4.7.2 a starší verze <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> a <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> které jsou programově přidány do ovládacího prvku webformaci, <xref:System.Web.UI.WebControls.CheckBox> se po zpětném odeslání ztratí.</span><span class="sxs-lookup"><span data-stu-id="0a100-103">For applications that target .NET Framework 4.7.2 and earlier versions, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> that are programmatically added to a WebForms <xref:System.Web.UI.WebControls.CheckBox> control are lost after postback.</span></span> <span data-ttu-id="0a100-104">Pro aplikace, které cílí na .NET Framework 4,8 nebo novější verze, se po zpětném odeslání uchovávají.</span><span class="sxs-lookup"><span data-stu-id="0a100-104">For applications that target .NET Framework 4.8 or later versions, they are preserved after postback.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0a100-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="0a100-105">Suggestion</span></span>

<span data-ttu-id="0a100-106">Pro správné chování při obnovování atributů při zpětném volání nastavte na <code>targetFrameworkVersion</code> 4,8 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="0a100-106">For the correct behavior for restoring attributes on postback, set the <code>targetFrameworkVersion</code> to 4.8 or higher.</span></span> <span data-ttu-id="0a100-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0a100-107">For example:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="0a100-108">Jeho nastavení je nižší nebo vůbec nezachovává staré nesprávné chování.</span><span class="sxs-lookup"><span data-stu-id="0a100-108">Setting it lower, or not at all, preserves the old incorrect behavior.</span></span>

| <span data-ttu-id="0a100-109">Name</span><span class="sxs-lookup"><span data-stu-id="0a100-109">Name</span></span>    | <span data-ttu-id="0a100-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0a100-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0a100-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="0a100-111">Scope</span></span>   |<span data-ttu-id="0a100-112">Není známo</span><span class="sxs-lookup"><span data-stu-id="0a100-112">Unknown</span></span>|
|<span data-ttu-id="0a100-113">Verze</span><span class="sxs-lookup"><span data-stu-id="0a100-113">Version</span></span>|<span data-ttu-id="0a100-114">4,8</span><span class="sxs-lookup"><span data-stu-id="0a100-114">4.8</span></span>|
|<span data-ttu-id="0a100-115">Typ</span><span class="sxs-lookup"><span data-stu-id="0a100-115">Type</span></span>|<span data-ttu-id="0a100-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="0a100-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0a100-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0a100-117">Affected APIs</span></span>

-<xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
