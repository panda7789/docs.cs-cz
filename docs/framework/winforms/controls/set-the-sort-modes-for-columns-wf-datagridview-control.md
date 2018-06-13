---
title: 'Postupy: Nastavení režimů třídění pro sloupce v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 08d90bb45006af798b629f58821cbf50ee9ef089
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535728"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1f067-102">Postupy: Nastavení režimů třídění pro sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f067-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1f067-103">V <xref:System.Windows.Forms.DataGridView> řízení, textové pole sloupců použít automatické řazení ve výchozím nastavení, zatímco jiné typy sloupců nejsou automaticky seřazeny.</span><span class="sxs-lookup"><span data-stu-id="1f067-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="1f067-104">Někdy budete chtít přepsat tyto výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1f067-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="1f067-105">Například můžete zobrazit obrázky místo textu, čísla nebo hodnoty výčtu buněk.</span><span class="sxs-lookup"><span data-stu-id="1f067-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="1f067-106">Při bitové kopie nelze řadit, základní hodnoty, které představují lze seřadit.</span><span class="sxs-lookup"><span data-stu-id="1f067-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="1f067-107">V <xref:System.Windows.Forms.DataGridView> ovládací prvek, <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> hodnota vlastnosti sloupce určuje jeho řazení chování.</span><span class="sxs-lookup"><span data-stu-id="1f067-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="1f067-108">Následující postup ukazuje `Priority` sloupec z [postupy: přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1f067-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="1f067-109">Tento sloupec je sloupec bitové kopie a není ve výchozím nastavení řazení.</span><span class="sxs-lookup"><span data-stu-id="1f067-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="1f067-110">Obsahuje hodnoty skutečné buněk, které jsou řetězce, ale tak může být seřazeny automaticky.</span><span class="sxs-lookup"><span data-stu-id="1f067-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="1f067-111">Chcete-li nastavit režim řazení pro sloupec</span><span class="sxs-lookup"><span data-stu-id="1f067-111">To set the sort mode for a column</span></span>  
  
-   <span data-ttu-id="1f067-112">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1f067-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1f067-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1f067-113">Compiling the Code</span></span>  
 <span data-ttu-id="1f067-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1f067-114">This example requires:</span></span>  
  
-   <span data-ttu-id="1f067-115">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , který obsahuje sloupec s názvem `Priority`.</span><span class="sxs-lookup"><span data-stu-id="1f067-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
-   <span data-ttu-id="1f067-116">Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f067-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f067-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f067-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="1f067-118">Řazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f067-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1f067-119">Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f067-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1f067-120">Postupy: Přizpůsobení řazení v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1f067-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
