---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567344"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="22c0c-101">Pokud je zobrazený popis, událost CellFormatting se neaktivuje.</span><span class="sxs-lookup"><span data-stu-id="22c0c-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="22c0c-102"><xref:System.Windows.Forms.DataGridView> nyní zobrazuje text buňky a popisky chyb, když je najede myší a když je vyberete prostřednictvím klávesnice.</span><span class="sxs-lookup"><span data-stu-id="22c0c-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="22c0c-103">Pokud se zobrazí popis, událost <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> se neaktivuje.</span><span class="sxs-lookup"><span data-stu-id="22c0c-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="22c0c-104">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="22c0c-104">Change description</span></span>

<span data-ttu-id="22c0c-105">Před rozhraním .NET Core 3,1 se <xref:System.Windows.Forms.DataGridView>, která měla vlastnost <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> nastavená na `true`, ukázala popis pro text buňky a chyby, když buňka nacházela myší.</span><span class="sxs-lookup"><span data-stu-id="22c0c-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="22c0c-106">Při výběru buňky prostřednictvím klávesnice (například pomocí klávesy TAB, klávesových zkratek nebo navigace pomocí šipky) nebyly zobrazeny popisy tlačítek.</span><span class="sxs-lookup"><span data-stu-id="22c0c-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="22c0c-107">Pokud uživatel upravil buňku a poté, <xref:System.Windows.Forms.DataGridView> byla v režimu úprav ponechána nad buňkou, která nemá nastavenou vlastnost <xref:System.Windows.Forms.DataGridViewCell.ToolTipText>, byla vyvolána událost <xref:System.Windows.Forms.DataGridView.CellFormatting> pro formátování textu buňky pro zobrazení v buňce.</span><span class="sxs-lookup"><span data-stu-id="22c0c-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="22c0c-108">Aby se dosáhlo standardů přístupnosti, počínaje platformou .NET Core 3,1, <xref:System.Windows.Forms.DataGridView>, která má vlastnost <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> nastavenou na `true`, se zobrazí popisy textu buňky a chyby, které nejsou jenom v případě, že je buňka najetí myší, ale také když se vybere přes klávesnici.</span><span class="sxs-lookup"><span data-stu-id="22c0c-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="22c0c-109">V důsledku této změny se událost <xref:System.Windows.Forms.DataGridView.CellFormatting> *nevygeneruje* , když se buňky, které nemají sadu vlastností <xref:System.Windows.Forms.DataGridViewCell.ToolTipText>, nepřesunou myší, zatímco <xref:System.Windows.Forms.DataGridView> je v režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="22c0c-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="22c0c-110">Událost není vyvolána, protože obsah buňky najetí myší se zobrazí jako popisek namísto zobrazení v buňce.</span><span class="sxs-lookup"><span data-stu-id="22c0c-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="22c0c-111">Představená verze</span><span class="sxs-lookup"><span data-stu-id="22c0c-111">Version introduced</span></span>

<span data-ttu-id="22c0c-112">3,1</span><span class="sxs-lookup"><span data-stu-id="22c0c-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="22c0c-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="22c0c-113">Recommended action</span></span>

<span data-ttu-id="22c0c-114">Refaktorujte jakýkoli kód, který závisí na události <xref:System.Windows.Forms.DataGridView.CellFormatting>, zatímco <xref:System.Windows.Forms.DataGridView> je v režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="22c0c-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="22c0c-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="22c0c-115">Category</span></span>

<span data-ttu-id="22c0c-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="22c0c-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="22c0c-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="22c0c-117">Affected APIs</span></span>

<span data-ttu-id="22c0c-118">Nedá se detekovat přes analýzu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="22c0c-118">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
