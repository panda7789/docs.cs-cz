---
ms.openlocfilehash: 0ef39d67cd4335658658f5772b5bce49d827cad0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614597"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a><span data-ttu-id="97e36-101">Událost SelectionChanged a vlastnost SelectedValue selektoru</span><span class="sxs-lookup"><span data-stu-id="97e36-101">Selector SelectionChanged event and SelectedValue property</span></span>

#### <a name="details"></a><span data-ttu-id="97e36-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="97e36-102">Details</span></span>

<span data-ttu-id="97e36-103">Počínaje .NET Framework 4.7.1, <xref:System.Windows.Controls.Primitives.Selector> vždy aktualizuje hodnotu vlastnosti před vyvoláním <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> události, když se změní její výběr.</span><span class="sxs-lookup"><span data-stu-id="97e36-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.Primitives.Selector> always updates the value of its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.</span></span> <span data-ttu-id="97e36-104">Tím se vlastnost SelectedValue v souladu s ostatními vlastnostmi výběru ( <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> a <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> ), které jsou před vyvoláním události aktualizovány.</span><span class="sxs-lookup"><span data-stu-id="97e36-104">This makes the SelectedValue property consistent with the other selection properties (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> and <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), which are updated before raising the event.</span></span><p/><span data-ttu-id="97e36-105">V .NET Framework 4,7 a dřívějších verzích nastala aktualizace SelectedValue před událostí ve většině případů, ale ta se stala po události, kdy Změna výběru byla způsobena změnou <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="97e36-105">In the .NET Framework 4.7 and earlier versions, the update to SelectedValue happened before the event in most cases, but it happened after the event if the selection change was caused by changing the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="97e36-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="97e36-106">Suggestion</span></span>

<span data-ttu-id="97e36-107">Aplikace, které cílí na .NET Framework 4.7.1 nebo novější, si mohou tuto změnu odhlásit a použít starší chování tak, že do `<runtime>` části konfiguračního souboru aplikace přidáte následující:</span><span class="sxs-lookup"><span data-stu-id="97e36-107">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the `<runtime>` section of the application configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="97e36-108">Aplikace, které cílí na .NET Framework 4,7 nebo starší, ale běží na .NET Framework 4.7.1 nebo novějším, můžou nové chování povolit přidáním následujícího řádku do `<runtime>` oddílu souboru Application. Configuration:</span><span class="sxs-lookup"><span data-stu-id="97e36-108">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="97e36-109">Name</span><span class="sxs-lookup"><span data-stu-id="97e36-109">Name</span></span>    | <span data-ttu-id="97e36-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="97e36-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="97e36-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="97e36-111">Scope</span></span>   | <span data-ttu-id="97e36-112">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="97e36-112">Minor</span></span>       |
| <span data-ttu-id="97e36-113">Verze</span><span class="sxs-lookup"><span data-stu-id="97e36-113">Version</span></span> | <span data-ttu-id="97e36-114">4.7.1</span><span class="sxs-lookup"><span data-stu-id="97e36-114">4.7.1</span></span>       |
| <span data-ttu-id="97e36-115">Typ</span><span class="sxs-lookup"><span data-stu-id="97e36-115">Type</span></span>    | <span data-ttu-id="97e36-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="97e36-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="97e36-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="97e36-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
