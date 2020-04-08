---
ms.openlocfilehash: b736ab743a628fdcbc53c5ee51551e5dad986885
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888110"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="eb3af-101">Událost CellFormatting není vyvolána, pokud je zobrazen popisek</span><span class="sxs-lookup"><span data-stu-id="eb3af-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="eb3af-102">A <xref:System.Windows.Forms.DataGridView> nyní zobrazuje text buňky a popisky chyb, když je hovered myší a když je vybrán pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="eb3af-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="eb3af-103">Pokud je zobrazen popisek, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událost není vyvolána.</span><span class="sxs-lookup"><span data-stu-id="eb3af-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="eb3af-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="eb3af-104">Change description</span></span>

<span data-ttu-id="eb3af-105">Před .NET Core 3.1, <xref:System.Windows.Forms.DataGridView> který <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> měl `true` vlastnost nastavenou na zobrazení popisku pro text buňky a chyby, když byla buňka jehována myší.</span><span class="sxs-lookup"><span data-stu-id="eb3af-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="eb3af-106">Popisky nebyly zobrazeny, když byla buňka vybrána pomocí klávesnice (například pomocí klávesy Tab, klávesových zkratek nebo navigace se šipkami).</span><span class="sxs-lookup"><span data-stu-id="eb3af-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="eb3af-107">Pokud uživatel upravil buňku a poté, když <xref:System.Windows.Forms.DataGridView> byl ještě v režimu úprav, se <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> pohyboval nad <xref:System.Windows.Forms.DataGridView.CellFormatting> buňkou, která neměla nastavenou vlastnost, byla vyvolána událost, která formátuje text buňky pro zobrazení v buňce.</span><span class="sxs-lookup"><span data-stu-id="eb3af-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="eb3af-108">Chcete-li splnit standardy usnadnění přístupu, <xref:System.Windows.Forms.DataGridView> počínaje .NET Core 3.1, který má <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> vlastnost nastavena na `true` zobrazení popisů pro text buňky a chyby nejen při pohyblivosti buňky, ale také když je vybrána pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="eb3af-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="eb3af-109">V důsledku této změny <xref:System.Windows.Forms.DataGridView.CellFormatting> *není* událost vyvolána, když jsou <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> buňky, které nemají <xref:System.Windows.Forms.DataGridView> sadu vlastností, vztyčeny, když je v režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="eb3af-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="eb3af-110">Událost není vyvolána, protože obsah buňky s odkazem je zobrazen jako popisek namísto zobrazení v buňce.</span><span class="sxs-lookup"><span data-stu-id="eb3af-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eb3af-111">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="eb3af-111">Version introduced</span></span>

<span data-ttu-id="eb3af-112">3.1</span><span class="sxs-lookup"><span data-stu-id="eb3af-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eb3af-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="eb3af-113">Recommended action</span></span>

<span data-ttu-id="eb3af-114">Refaktorovat jakýkoli kód, <xref:System.Windows.Forms.DataGridView.CellFormatting> který <xref:System.Windows.Forms.DataGridView> závisí na události, zatímco je v režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="eb3af-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="eb3af-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="eb3af-115">Category</span></span>

<span data-ttu-id="eb3af-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eb3af-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eb3af-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="eb3af-117">Affected APIs</span></span>

<span data-ttu-id="eb3af-118">Žádný</span><span class="sxs-lookup"><span data-stu-id="eb3af-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis.

-->
