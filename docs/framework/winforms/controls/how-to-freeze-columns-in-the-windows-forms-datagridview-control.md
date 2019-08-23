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
ms.openlocfilehash: a83c5078d67be40fda2ae3382b8124594ee78103
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966650"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="74bd6-102">Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="74bd6-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="74bd6-103">Když uživatelé zobrazují data zobrazená v ovládacím <xref:System.Windows.Forms.DataGridView> prvku model Windows Forms, někdy potřebují často odkazovat na jeden sloupec nebo na sadu sloupců.</span><span class="sxs-lookup"><span data-stu-id="74bd6-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="74bd6-104">Když například zobrazíte tabulku s informacemi o zákaznících, které obsahují mnoho sloupců, je vhodné zobrazit jméno zákazníka vždy, když se ostatní sloupce posouvají mimo viditelnou oblast.</span><span class="sxs-lookup"><span data-stu-id="74bd6-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="74bd6-105">Chcete-li dosáhnout tohoto chování, můžete ukotvit sloupce v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="74bd6-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="74bd6-106">Při ukotvení sloupce jsou zmrazeny také všechny sloupce vlevo (nebo napravo ve skriptech se zápisem zprava doleva).</span><span class="sxs-lookup"><span data-stu-id="74bd6-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="74bd6-107">Zmrazené sloupce zůstávají na místě, zatímco všechny ostatní sloupce se můžou posouvat.</span><span class="sxs-lookup"><span data-stu-id="74bd6-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74bd6-108">Pokud je povoleno přeřazení sloupce, jsou zmrazené sloupce považovány za skupinu odlišnou od nezmrazených sloupců.</span><span class="sxs-lookup"><span data-stu-id="74bd6-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="74bd6-109">Uživatelé mohou přemístit sloupce v obou skupinách, ale nemohou přesunout sloupec z jedné skupiny do druhé.</span><span class="sxs-lookup"><span data-stu-id="74bd6-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="74bd6-110"><xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Vlastnost sloupce určuje, zda je sloupec v mřížce vždy zobrazen.</span><span class="sxs-lookup"><span data-stu-id="74bd6-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="74bd6-111">Pro tuto úlohu se v aplikaci Visual Studio podporuje.</span><span class="sxs-lookup"><span data-stu-id="74bd6-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="74bd6-112">Podívejte [se také na postupy: Ukotvit sloupce v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](freeze-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="74bd6-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](freeze-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="74bd6-113">Postup zmrazení sloupce prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="74bd6-113">To freeze a column programmatically</span></span>  
  
- <span data-ttu-id="74bd6-114">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="74bd6-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="74bd6-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="74bd6-115">Compiling the Code</span></span>  
 <span data-ttu-id="74bd6-116">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="74bd6-116">This example requires:</span></span>  
  
- <span data-ttu-id="74bd6-117">Ovládací prvek s `dataGridView1` názvem, který obsahuje sloupec s názvem `AddToCartButton`. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="74bd6-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
- <span data-ttu-id="74bd6-118">Odkazy na <xref:System?displayProperty=nameWithType> sestavení a <xref:System.Windows.Forms?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="74bd6-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74bd6-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74bd6-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="74bd6-120">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="74bd6-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="74bd6-121">Postupy: Povolit změnu pořadí sloupců v ovládacím prvku DataGridView model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74bd6-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
