---
title: Nastavit sloupce jen pro čtení v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: 11d008d47ec5edb594d3d862c68ff3b9920e0e25
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736181"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="edf99-102">Postupy: Přepnutí sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="edf99-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="edf99-103">Ne všechna data jsou určena pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="edf99-103">Not all data is meant for editing.</span></span> <span data-ttu-id="edf99-104">V ovládacím prvku <xref:System.Windows.Forms.DataGridView> vlastnost <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> sloupce určuje, zda uživatelé mohou upravovat buňky v tomto sloupci.</span><span class="sxs-lookup"><span data-stu-id="edf99-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="edf99-105">Informace o tom, jak nastavit ovládací prvek jen pro čtení, naleznete [v tématu How to: prevence a Dissčítání řádků v ovládacím prvku DataGridView model Windows Forms](prevent-row-addition-and-deletion-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="edf99-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="edf99-106">Pro tuto úlohu se v aplikaci Visual Studio podporuje.</span><span class="sxs-lookup"><span data-stu-id="edf99-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="edf99-107">Přečtěte si také téma [How to: zpřístupnit sloupce jen pro čtení v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="edf99-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="edf99-108">Zpřístupnění sloupce pouze pro čtení prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="edf99-108">To make a column read-only programmatically</span></span>  
  
- <span data-ttu-id="edf99-109">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="edf99-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="edf99-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="edf99-110">Compiling the Code</span></span>  
 <span data-ttu-id="edf99-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="edf99-111">This example requires:</span></span>  
  
- <span data-ttu-id="edf99-112"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` se sloupcem s názvem `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="edf99-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
- <span data-ttu-id="edf99-113">Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="edf99-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf99-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="edf99-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="edf99-115">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="edf99-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="edf99-116">Postupy: Zamezení přidávání a odstraňování řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="edf99-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](prevent-row-addition-and-deletion-datagridview.md)
