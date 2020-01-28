---
title: Přidání popisů do jednotlivých buněk v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: ac86db5fa27a95adb20888cd59b5e236941d9177
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732178"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="52f10-102">Postupy: Přidání ToolTips do jednotlivých buněk v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="52f10-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="52f10-103">Ve výchozím nastavení se pro zobrazení jejich celého obsahu používají popisy tlačítek pro zobrazení hodnot <xref:System.Windows.Forms.DataGridView> buněk, které jsou příliš malé.</span><span class="sxs-lookup"><span data-stu-id="52f10-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="52f10-104">Toto chování však můžete přepsat pro nastavení textových hodnot popisku pro jednotlivé buňky.</span><span class="sxs-lookup"><span data-stu-id="52f10-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="52f10-105">To je užitečné, když chcete uživatelům zobrazit další informace o buňce nebo uživatelům poskytnout alternativní popis obsahu buňky.</span><span class="sxs-lookup"><span data-stu-id="52f10-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="52f10-106">Například pokud máte řádek, který zobrazuje ikony stavu, možná budete chtít zadat vysvětlení textu pomocí popisů tlačítek.</span><span class="sxs-lookup"><span data-stu-id="52f10-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="52f10-107">Zobrazení popisků na úrovni buňky můžete také zakázat nastavením vlastnosti <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> na `false`.</span><span class="sxs-lookup"><span data-stu-id="52f10-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="52f10-108">Přidání popisu k buňce</span><span class="sxs-lookup"><span data-stu-id="52f10-108">To add a ToolTip to a cell</span></span>  
  
- <span data-ttu-id="52f10-109">Nastavte vlastnost <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="52f10-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="52f10-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="52f10-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="52f10-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="52f10-111">This example requires:</span></span>  
  
- <span data-ttu-id="52f10-112"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`, který obsahuje sloupec s názvem `Rating` pro zobrazení hodnot řetězce na jednom až čtyř symbol hvězdičky ("\*").</span><span class="sxs-lookup"><span data-stu-id="52f10-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("\*") symbols.</span></span> <span data-ttu-id="52f10-113">Událost <xref:System.Windows.Forms.DataGridView.CellFormatting> ovládacího prvku musí být přidružena k metodě obslužné rutiny události zobrazené v příkladu.</span><span class="sxs-lookup"><span data-stu-id="52f10-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
- <span data-ttu-id="52f10-114">Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="52f10-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="52f10-115">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="52f10-115">Robust Programming</span></span>  
 <span data-ttu-id="52f10-116">Při vázání ovládacího prvku <xref:System.Windows.Forms.DataGridView> k externímu zdroji dat nebo poskytnutí vlastního zdroje dat implementací virtuálního režimu může dojít k problémům s výkonem.</span><span class="sxs-lookup"><span data-stu-id="52f10-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="52f10-117">Aby se zabránilo snížení výkonu při práci s velkým množstvím dat, zpracujte <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> událost namísto nastavení vlastnosti <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> více buněk.</span><span class="sxs-lookup"><span data-stu-id="52f10-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="52f10-118">Při zpracování této události, získání hodnoty vlastnosti <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> buňky vyvolá událost a vrátí hodnotu vlastnosti <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType>, jak je uvedeno v obslužné rutině události.</span><span class="sxs-lookup"><span data-stu-id="52f10-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f10-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52f10-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="52f10-120">Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="52f10-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
