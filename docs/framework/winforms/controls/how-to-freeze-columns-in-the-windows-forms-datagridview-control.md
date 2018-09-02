---
title: 'Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: df8ac7e7db74d4e8df8872b5ec7f8f2ec774b3c8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407295"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="08aa2-102">Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="08aa2-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="08aa2-103">Když uživatelé zobrazit data zobrazená ve Windows Forms <xref:System.Windows.Forms.DataGridView> ovládacího prvku, někdy potřebují často odkazovat na jeden sloupec nebo sadu sloupců.</span><span class="sxs-lookup"><span data-stu-id="08aa2-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="08aa2-104">Například při zobrazení informací o zákaznících, který obsahuje mnoho sloupců tabulky, je užitečné zobrazit název zákazníka po celou dobu při povolení další sloupce mimo viditelná oblast.</span><span class="sxs-lookup"><span data-stu-id="08aa2-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="08aa2-105">K dosažení tohoto chování, lze ukotvit sloupce v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="08aa2-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="08aa2-106">Po ukotvení sloupce jsou zmražená i všechny sloupce na levé straně (nebo vpravo v skripty jazyka zprava doleva).</span><span class="sxs-lookup"><span data-stu-id="08aa2-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="08aa2-107">Zmrazené sloupce zůstanou na místě, zatímco všechny ostatní sloupce můžete posouvat.</span><span class="sxs-lookup"><span data-stu-id="08aa2-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08aa2-108">Pokud je zapnutá změnu pořadí sloupců, zmrazené sloupce jsou považovány za skupiny, která se liší od nezmrazeném sloupci.</span><span class="sxs-lookup"><span data-stu-id="08aa2-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="08aa2-109">Uživatelům můžete přemístit sloupce v jedné skupině, ale sloupce z jedné skupiny nemůže přesunout do jiné.</span><span class="sxs-lookup"><span data-stu-id="08aa2-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="08aa2-110"><xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Vlastnost sloupec určuje, zda sloupec je vždy zobrazen v mřížce.</span><span class="sxs-lookup"><span data-stu-id="08aa2-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="08aa2-111">Není poskytována podpora pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="08aa2-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="08aa2-112">Viz také [postupy: zablokování sloupců v Windows Forms DataGridView ovládacího prvku pomocí návrháře](https://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="08aa2-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="08aa2-113">Chcete-li ukotvit sloupec prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="08aa2-113">To freeze a column programmatically</span></span>  
  
-   <span data-ttu-id="08aa2-114">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="08aa2-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="08aa2-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="08aa2-115">Compiling the Code</span></span>  
 <span data-ttu-id="08aa2-116">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="08aa2-116">This example requires:</span></span>  
  
-   <span data-ttu-id="08aa2-117">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , která obsahuje sloupec s názvem `AddToCartButton`.</span><span class="sxs-lookup"><span data-stu-id="08aa2-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
-   <span data-ttu-id="08aa2-118">Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="08aa2-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08aa2-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="08aa2-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="08aa2-120">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="08aa2-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="08aa2-121">Postupy: Povolení změny pořadí v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="08aa2-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
