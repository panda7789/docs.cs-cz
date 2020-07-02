---
ms.openlocfilehash: f4ff938b2d0e9ead481fdf239aed8a6b918a99b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620093"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a><span data-ttu-id="94af7-101">ListBoxItem problém vazby s kolekci ObservableCollection &lt; T &gt; . Pøesunout</span><span class="sxs-lookup"><span data-stu-id="94af7-101">ListBoxItem IsSelected binding issue with ObservableCollection&lt;T&gt;.Move</span></span>

#### <a name="details"></a><span data-ttu-id="94af7-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="94af7-102">Details</span></span>

<span data-ttu-id="94af7-103">Volání <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> nebo <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> na kolekci vázané k <xref:System.Windows.Controls.ListBox?displayProperty=fullName> vybraným položkám může vést k nestabilnímu chování s budoucím výběrem nebo bez výběru <xref:System.Windows.Controls.ListBox?displayProperty=fullName> položek.</span><span class="sxs-lookup"><span data-stu-id="94af7-103">Calling <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> or <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> on a collection bound to a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> with items selected can lead to erratic behavior with future selection or unselection of <xref:System.Windows.Controls.ListBox?displayProperty=fullName> items.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="94af7-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="94af7-104">Suggestion</span></span>

<span data-ttu-id="94af7-105">Volání <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> a <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> místo toho <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> bude tento problém obejít.</span><span class="sxs-lookup"><span data-stu-id="94af7-105">Calling <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> and <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> instead of <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> will work around this issue.</span></span> <span data-ttu-id="94af7-106">Případně byl tento problém opravený v .NET Framework 4,6 a může se řešit upgradem na verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94af7-106">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="94af7-107">Name</span><span class="sxs-lookup"><span data-stu-id="94af7-107">Name</span></span>    | <span data-ttu-id="94af7-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="94af7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="94af7-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="94af7-109">Scope</span></span>   |<span data-ttu-id="94af7-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="94af7-110">Minor</span></span>|
|<span data-ttu-id="94af7-111">Verze</span><span class="sxs-lookup"><span data-stu-id="94af7-111">Version</span></span>|<span data-ttu-id="94af7-112">4.5</span><span class="sxs-lookup"><span data-stu-id="94af7-112">4.5</span></span>|
|<span data-ttu-id="94af7-113">Typ</span><span class="sxs-lookup"><span data-stu-id="94af7-113">Type</span></span>|<span data-ttu-id="94af7-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="94af7-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="94af7-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="94af7-115">Affected APIs</span></span>

-<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
