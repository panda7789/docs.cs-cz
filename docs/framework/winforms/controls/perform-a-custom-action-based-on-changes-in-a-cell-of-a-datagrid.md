---
title: 'Postupy: Provedení vlastní akce na základě změn v buňce ovládacího prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
ms.openlocfilehash: ad1c60c34fc5461de21e2ad5d4d02f5b2abd6dfd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705581"
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a><span data-ttu-id="837f5-102">Postupy: Provedení vlastní akce na základě změn v buňce ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="837f5-102">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="837f5-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek má několik událostí můžete použít k detekci změn stavu <xref:System.Windows.Forms.DataGridView> buňky.</span><span class="sxs-lookup"><span data-stu-id="837f5-103">The <xref:System.Windows.Forms.DataGridView> control has a number of events you can use to detect changes in the state of <xref:System.Windows.Forms.DataGridView> cells.</span></span> <span data-ttu-id="837f5-104">Dva z nejčastěji používané jsou <xref:System.Windows.Forms.DataGridView.CellValueChanged> a <xref:System.Windows.Forms.DataGridView.CellStateChanged> události.</span><span class="sxs-lookup"><span data-stu-id="837f5-104">Two of the most commonly used are the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a><span data-ttu-id="837f5-105">Ke zjištění změny hodnoty buněk DataGridView</span><span class="sxs-lookup"><span data-stu-id="837f5-105">To detect changes in the values of DataGridView cells</span></span>  
  
-   <span data-ttu-id="837f5-106">Zápis obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellValueChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="837f5-106">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellValueChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a><span data-ttu-id="837f5-107">Ke zjištění změny ve stavu buněk DataGridView</span><span class="sxs-lookup"><span data-stu-id="837f5-107">To detect changes in the states of DataGridView cells</span></span>  
  
-   <span data-ttu-id="837f5-108">Zápis obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellStateChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="837f5-108">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellStateChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="837f5-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="837f5-109">Compiling the Code</span></span>  
 <span data-ttu-id="837f5-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="837f5-110">This example requires:</span></span>  
  
-   <span data-ttu-id="837f5-111">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="837f5-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span> <span data-ttu-id="837f5-112">Pro C#, obslužné rutiny událostí musí být připojený k odpovídající události.</span><span class="sxs-lookup"><span data-stu-id="837f5-112">For C#, the event handlers must be connected to the corresponding events.</span></span>  
  
-   <span data-ttu-id="837f5-113">Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="837f5-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="837f5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="837f5-114">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>
- [<span data-ttu-id="837f5-115">Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="837f5-115">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
- [<span data-ttu-id="837f5-116">Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="837f5-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
