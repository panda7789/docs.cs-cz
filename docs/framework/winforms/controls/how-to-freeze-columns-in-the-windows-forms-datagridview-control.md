---
title: "Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: baf2b0218c1818d6a92ca7790c8c50bd94ecfd9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5dc2e-102">Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5dc2e-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5dc2e-103">Když uživatelé zobrazit data zobrazená v systému Windows Forms <xref:System.Windows.Forms.DataGridView> ovládací prvek, někdy potřebují k odkazování na jeden sloupec nebo sadu sloupců často.</span><span class="sxs-lookup"><span data-stu-id="5dc2e-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="5dc2e-104">Například při zobrazení tabulku informace o zákazníkovi, který obsahuje mnoho sloupců, je vhodné zobrazované jméno zákazníka za všech okolností při povolování ostatních sloupců posun mimo oblast viditelné.</span><span class="sxs-lookup"><span data-stu-id="5dc2e-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="5dc2e-105">K dosažení toto chování, můžete zmrazení sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="5dc2e-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="5dc2e-106">Po ukotvení sloupec se všechny sloupce na levé straně, (nebo záhlavím vpravo ve skriptech jazyk zprava doleva) jsou také pozastaveny.</span><span class="sxs-lookup"><span data-stu-id="5dc2e-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="5dc2e-107">Ukotvené sloupce, takže zůstávají na svém místě, při lze posunout všech ostatních sloupců.</span><span class="sxs-lookup"><span data-stu-id="5dc2e-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5dc2e-108">Pokud je povoleno změny pořadí sloupců, ukotvené sloupce jsou považovány za skupinu liší od neukotvené sloupce.</span><span class="sxs-lookup"><span data-stu-id="5dc2e-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="5dc2e-109">Uživatelé mohou změnit umístění sloupce buď skupiny, ale sloupec nemůže přesunout z jedné skupiny na druhý.</span><span class="sxs-lookup"><span data-stu-id="5dc2e-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="5dc2e-110"><xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Vlastnost sloupce určuje, zda sloupec je vždy zobrazen v mřížce.</span><span class="sxs-lookup"><span data-stu-id="5dc2e-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="5dc2e-111">Není poskytována podpora pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5dc2e-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="5dc2e-112">Informace v tématu [postupy: zablokování sloupců v Windows Forms DataGridView – ovládací prvek pomocí návrháře](http://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5dc2e-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="5dc2e-113">Chcete-li ukotvit sloupec prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="5dc2e-113">To freeze a column programmatically</span></span>  
  
-   <span data-ttu-id="5dc2e-114">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="5dc2e-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5dc2e-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5dc2e-115">Compiling the Code</span></span>  
 <span data-ttu-id="5dc2e-116">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="5dc2e-116">This example requires:</span></span>  
  
-   <span data-ttu-id="5dc2e-117">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , který obsahuje sloupec s názvem `AddToCartButton`.</span><span class="sxs-lookup"><span data-stu-id="5dc2e-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
-   <span data-ttu-id="5dc2e-118">Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="5dc2e-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dc2e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="5dc2e-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="5dc2e-120">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5dc2e-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="5dc2e-121">Postupy: povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5dc2e-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
