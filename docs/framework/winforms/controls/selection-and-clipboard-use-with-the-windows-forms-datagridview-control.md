---
title: Výběr a použití schránky s ovládacím prvkem DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
ms.openlocfilehash: 6993f77e8ce532d8df1bdc7e6b6abc1cc3268e49
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743059"
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="a4c68-102">Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a4c68-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a4c68-103">Ovládací prvek `DataGridView` poskytuje celou řadu možností pro konfiguraci způsobu, jakým uživatelé mohou vybírat buňky, řádky a sloupce.</span><span class="sxs-lookup"><span data-stu-id="a4c68-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="a4c68-104">Můžete například povolit jeden nebo vícenásobný výběr, výběr celých řádků nebo sloupců, když uživatel klikne na buňky, nebo na výběr celých řádků nebo sloupců, pouze když uživatel klikne na záhlaví, což umožňuje výběr buňky také.</span><span class="sxs-lookup"><span data-stu-id="a4c68-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="a4c68-105">Chcete-li pro výběr zadat vlastní uživatelské rozhraní, můžete vypnout běžný výběr a zpracovat veškerý výběr programově.</span><span class="sxs-lookup"><span data-stu-id="a4c68-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="a4c68-106">Kromě toho můžete uživatelům povolit kopírování vybraných hodnot do schránky.</span><span class="sxs-lookup"><span data-stu-id="a4c68-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4c68-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a4c68-107">In This Section</span></span>  
 [<span data-ttu-id="a4c68-108">Režimy výběru v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a4c68-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a4c68-109">Popisuje možnosti pro uživatele a programový výběr v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="a4c68-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="a4c68-110">Postupy: Nastavení režimu výběru ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a4c68-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a4c68-111">Popisuje způsob konfigurace ovládacího prvku pro výběr s jedním řádkem, když uživatel klikne na buňku.</span><span class="sxs-lookup"><span data-stu-id="a4c68-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="a4c68-112">Postupy: Získání vybraných buněk, řádků a sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a4c68-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="a4c68-113">Popisuje, jak pracovat s vybranými kolekcemi buněk, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="a4c68-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="a4c68-114">Postupy: Povolení kopírování více buněk do schránky z ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a4c68-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="a4c68-115">Popisuje, jak povolit podporu schránky v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="a4c68-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a4c68-116">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="a4c68-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="a4c68-117">Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="a4c68-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="a4c68-118">Poskytuje referenční dokumentaci pro vlastnost <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="a4c68-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="a4c68-119">Poskytuje referenční dokumentaci pro vlastnost <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="a4c68-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="a4c68-120">Poskytuje referenční dokumentaci pro třídu <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>.</span><span class="sxs-lookup"><span data-stu-id="a4c68-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="a4c68-121">Poskytuje referenční dokumentaci pro třídu <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>.</span><span class="sxs-lookup"><span data-stu-id="a4c68-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="a4c68-122">Poskytuje referenční dokumentaci pro třídu <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="a4c68-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c68-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4c68-123">See also</span></span>

- [<span data-ttu-id="a4c68-124">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="a4c68-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="a4c68-125">Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a4c68-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
