---
ms.openlocfilehash: dfdb62e8dd6db67d4fd12aba93928f4615e3f284
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614605"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a><span data-ttu-id="0aee6-101">Událost TabControl SelectionChanged a vlastnost SelectedContent</span><span class="sxs-lookup"><span data-stu-id="0aee6-101">TabControl SelectionChanged event and SelectedContent property</span></span>

#### <a name="details"></a><span data-ttu-id="0aee6-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0aee6-102">Details</span></span>

<span data-ttu-id="0aee6-103">Počínaje .NET Framework 4.7.1 <xref:System.Windows.Controls.TabControl> aktualizuje hodnotu vlastnosti před vyvoláním <xref:System.Windows.Controls.TabControl.SelectedContent> <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> události, když se změní její výběr. V .NET Framework 4,7 a starších verzích se po události stala aktualizace SelectedContent.</span><span class="sxs-lookup"><span data-stu-id="0aee6-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.TabControl> updates the value of its <xref:System.Windows.Controls.TabControl.SelectedContent> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.In the .NET Framework 4.7 and earlier versions, the update to SelectedContent happened after the event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0aee6-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="0aee6-104">Suggestion</span></span>

<span data-ttu-id="0aee6-105">Aplikace, které cílí na .NET Framework 4.7.1 nebo novější, si mohou tuto změnu odhlásit a použít starší chování tak, že do `<runtime>` části konfiguračního souboru aplikace přidáte následující:</span><span class="sxs-lookup"><span data-stu-id="0aee6-105">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the `<runtime>` section of the application configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="0aee6-106">Aplikace, které cílí na .NET Framework 4,7 nebo starší, ale běží na .NET Framework 4.7.1 nebo novějším, můžou nové chování povolit přidáním následujícího řádku do `<runtime>` oddílu souboru Application. Configuration:</span><span class="sxs-lookup"><span data-stu-id="0aee6-106">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="0aee6-107">Name</span><span class="sxs-lookup"><span data-stu-id="0aee6-107">Name</span></span>    | <span data-ttu-id="0aee6-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0aee6-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0aee6-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="0aee6-109">Scope</span></span>   | <span data-ttu-id="0aee6-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="0aee6-110">Minor</span></span>       |
| <span data-ttu-id="0aee6-111">Verze</span><span class="sxs-lookup"><span data-stu-id="0aee6-111">Version</span></span> | <span data-ttu-id="0aee6-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="0aee6-112">4.7.1</span></span>       |
| <span data-ttu-id="0aee6-113">Typ</span><span class="sxs-lookup"><span data-stu-id="0aee6-113">Type</span></span>    | <span data-ttu-id="0aee6-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="0aee6-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0aee6-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0aee6-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
