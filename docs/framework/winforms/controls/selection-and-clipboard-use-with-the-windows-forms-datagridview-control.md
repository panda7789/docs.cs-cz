---
title: "Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ceea4108f39619ccbcbf0286905a94b8236607cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="a1525-102">Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a1525-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a1525-103">`DataGridView` Řízení nabízí řadu možností pro konfiguraci, jak mohou uživatelé vybrat buněk, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="a1525-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="a1525-104">Například můžete povolit výběr jednoho nebo více, výběr sloupce, když uživatelé kliknou na buňky nebo celou řádků nebo výběr celou řádků nebo sloupců jenom v případě, že uživatelé kliknou na jejich hlavičky, umožňující výběr buňky také.</span><span class="sxs-lookup"><span data-stu-id="a1525-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="a1525-105">Pokud chcete zadat vlastní uživatelské rozhraní pro výběr, můžete zakázat obyčejnou výběr a zpracování všech výběr prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="a1525-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="a1525-106">Kromě toho můžete povolit kopírování vybraných hodnot do schránky.</span><span class="sxs-lookup"><span data-stu-id="a1525-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1525-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a1525-107">In This Section</span></span>  
 [<span data-ttu-id="a1525-108">Režimy výběru v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a1525-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a1525-109">Popisuje možnosti pro uživatele a programové výběru v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="a1525-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="a1525-110">Postupy: Nastavení režimu výběru ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a1525-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a1525-111">Popisuje postup konfigurace ovládacího prvku pro výběr jednoho řádku, když uživatel klikne buňky.</span><span class="sxs-lookup"><span data-stu-id="a1525-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="a1525-112">Postupy: Získání vybraných buněk, řádků a sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a1525-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="a1525-113">Popisuje, jak pracovat s vybrané kolekce buněk, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="a1525-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="a1525-114">Postupy: Povolení kopírování více buněk do schránky z ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a1525-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="a1525-115">Popisuje, jak povolit podporu schránky v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="a1525-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a1525-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="a1525-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="a1525-117">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a1525-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="a1525-118">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a1525-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="a1525-119">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a1525-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="a1525-120">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="a1525-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="a1525-121">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="a1525-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="a1525-122">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="a1525-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1525-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1525-123">See Also</span></span>  
 [<span data-ttu-id="a1525-124">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="a1525-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="a1525-125">Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a1525-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
