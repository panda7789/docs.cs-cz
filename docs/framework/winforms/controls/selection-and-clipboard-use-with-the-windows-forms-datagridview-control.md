---
title: Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
ms.openlocfilehash: 61f3eee6f4690e9bd9141f2eeb6de330bac87550
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715370"
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="4cd4d-102">Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="4cd4d-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4cd4d-103">`DataGridView` Ovládacího prvku poskytuje širokou škálu možnosti konfigurace, jak mohou uživatelé vybrat buněk, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="4cd4d-104">Například můžete povolit jeden nebo více výběrů, výběr celého řádku nebo sloupce, když uživatelé kliknou na buňky nebo výběr celého řádku nebo sloupce pouze, když uživatelé kliknou na jeho záhlaví, umožňující výběr buněk také.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="4cd4d-105">Pokud chcete poskytnout vlastní uživatelské rozhraní pro výběr, můžete zakázat běžné výběru a výběr zpracovávat prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="4cd4d-106">Kromě toho můžete povolit kopírování vybraných hodnot do schránky.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4cd4d-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4cd4d-107">In This Section</span></span>  
 [<span data-ttu-id="4cd4d-108">Režimy výběru v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="4cd4d-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4cd4d-109">Popisuje možnosti pro uživatele a programové výběr v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="4cd4d-110">Postupy: Nastavení režimu výběru ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="4cd4d-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4cd4d-111">Popisuje postup konfigurace ovládacího prvku pro výběr jednoho řádku, když uživatel klikne na buňku.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="4cd4d-112">Postupy: Získání vybraných buněk, řádků a sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="4cd4d-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="4cd4d-113">Popisuje, jak pracovat s kolekcí vybraných buněk, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="4cd4d-114">Postupy: Povolit uživatelům kopírování více buněk do schránky z ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="4cd4d-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="4cd4d-115">Popisuje, jak povolit podporu schránky v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4cd4d-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="4cd4d-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="4cd4d-117">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="4cd4d-118">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="4cd4d-119">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="4cd4d-120">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="4cd4d-121">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="4cd4d-122">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="4cd4d-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd4d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cd4d-123">See also</span></span>
- [<span data-ttu-id="4cd4d-124">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="4cd4d-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="4cd4d-125">Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="4cd4d-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
