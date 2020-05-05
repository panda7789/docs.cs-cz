---
ms.openlocfilehash: b736ab743a628fdcbc53c5ee51551e5dad986885
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888110"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="c2f76-101">Pokud je zobrazený popis, událost CellFormatting se neaktivuje.</span><span class="sxs-lookup"><span data-stu-id="c2f76-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="c2f76-102">V <xref:System.Windows.Forms.DataGridView> této části se při stisknutí myši a při výběru přes klávesnici zobrazuje text buňky a popisky chyb.</span><span class="sxs-lookup"><span data-stu-id="c2f76-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="c2f76-103">Pokud je zobrazen popis tlačítka, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událost není vyvolána.</span><span class="sxs-lookup"><span data-stu-id="c2f76-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c2f76-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="c2f76-104">Change description</span></span>

<span data-ttu-id="c2f76-105">Před rozhraním .NET Core 3,1, <xref:System.Windows.Forms.DataGridView> u kterého byla <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> vlastnost nastavena na `true` hodnotu zobrazenou pomocí tlačítka pro text buňky a chyby, když byla buňka najeďte myší.</span><span class="sxs-lookup"><span data-stu-id="c2f76-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="c2f76-106">Při výběru buňky prostřednictvím klávesnice (například pomocí klávesy TAB, klávesových zkratek nebo navigace pomocí šipky) nebyly zobrazeny popisy tlačítek.</span><span class="sxs-lookup"><span data-stu-id="c2f76-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="c2f76-107">Pokud uživatel buňku upravil a potom v režimu úprav <xref:System.Windows.Forms.DataGridView> byl najeďte na buňku, která sadu <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> vlastností nevytvořila, byla vyvolána <xref:System.Windows.Forms.DataGridView.CellFormatting> událost, která naformátuje text buňky pro zobrazení v buňce.</span><span class="sxs-lookup"><span data-stu-id="c2f76-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="c2f76-108">Aby splňoval standard pro usnadnění přístupu, počínaje rozhraním .NET Core <xref:System.Windows.Forms.DataGridView> 3,1, které <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> má vlastnost nastavenou na, se `true` zobrazí popisy tlačítek pro text buňky a chyby, které nejsou jenom v případě, že je buňka najetí myší, ale také když se vybere přes klávesnici.</span><span class="sxs-lookup"><span data-stu-id="c2f76-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="c2f76-109">V <xref:System.Windows.Forms.DataGridView.CellFormatting> důsledku této *změny se událost neaktivuje* , pokud jsou buňky, které nemají sadu <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> vlastností, nepřesunuty, když <xref:System.Windows.Forms.DataGridView> je v režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="c2f76-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="c2f76-110">Událost není vyvolána, protože obsah buňky najetí myší se zobrazí jako popisek namísto zobrazení v buňce.</span><span class="sxs-lookup"><span data-stu-id="c2f76-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c2f76-111">Představená verze</span><span class="sxs-lookup"><span data-stu-id="c2f76-111">Version introduced</span></span>

<span data-ttu-id="c2f76-112">3.1</span><span class="sxs-lookup"><span data-stu-id="c2f76-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c2f76-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="c2f76-113">Recommended action</span></span>

<span data-ttu-id="c2f76-114">Refaktorujte jakýkoli kód, který závisí na <xref:System.Windows.Forms.DataGridView.CellFormatting> události, zatímco <xref:System.Windows.Forms.DataGridView> je v režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="c2f76-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="c2f76-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="c2f76-115">Category</span></span>

<span data-ttu-id="c2f76-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c2f76-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c2f76-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c2f76-117">Affected APIs</span></span>

<span data-ttu-id="c2f76-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="c2f76-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis.

-->
