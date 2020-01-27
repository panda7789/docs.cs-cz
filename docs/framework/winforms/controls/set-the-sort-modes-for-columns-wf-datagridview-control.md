---
title: Nastavení režimů řazení pro sloupce v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 45ee1e7d82f826cddbd3492fed0f63e7a9c2cf1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742995"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="09479-102">Postupy: Nastavení režimů třídění pro sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09479-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="09479-103">V ovládacím prvku <xref:System.Windows.Forms.DataGridView> sloupce textového pole používají automatické řazení ve výchozím nastavení, zatímco jiné typy sloupců se neřadí automaticky.</span><span class="sxs-lookup"><span data-stu-id="09479-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="09479-104">Někdy budete chtít přepsat tato výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="09479-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="09479-105">Například můžete zobrazit obrázky místo textu, čísel nebo hodnot buněk výčtu.</span><span class="sxs-lookup"><span data-stu-id="09479-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="09479-106">I když obrázky nelze seřadit, lze seřadit základní hodnoty, které představují.</span><span class="sxs-lookup"><span data-stu-id="09479-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="09479-107">V ovládacím prvku <xref:System.Windows.Forms.DataGridView> určuje hodnota vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> sloupce jeho chování při řazení.</span><span class="sxs-lookup"><span data-stu-id="09479-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="09479-108">Následující postup ukazuje sloupec `Priority` z tématu [Postupy: Přizpůsobení formátování dat v ovládacím prvku DataGridView model Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="09479-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="09479-109">Tento sloupec je sloupcem obrázku a ve výchozím nastavení není standardně zařadit.</span><span class="sxs-lookup"><span data-stu-id="09479-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="09479-110">Obsahuje skutečné hodnoty buňky, které jsou řetězce, ale lze je seřadit automaticky.</span><span class="sxs-lookup"><span data-stu-id="09479-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="09479-111">Nastavení režimu řazení pro sloupec</span><span class="sxs-lookup"><span data-stu-id="09479-111">To set the sort mode for a column</span></span>  
  
- <span data-ttu-id="09479-112">Nastavte vlastnost <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09479-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="09479-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="09479-113">Compiling the Code</span></span>  
 <span data-ttu-id="09479-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="09479-114">This example requires:</span></span>  
  
- <span data-ttu-id="09479-115"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`, který obsahuje sloupec s názvem `Priority`.</span><span class="sxs-lookup"><span data-stu-id="09479-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
- <span data-ttu-id="09479-116">Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="09479-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09479-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09479-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="09479-118">Řazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09479-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="09479-119">Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09479-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="09479-120">Postupy: Přizpůsobení řazení v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09479-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
