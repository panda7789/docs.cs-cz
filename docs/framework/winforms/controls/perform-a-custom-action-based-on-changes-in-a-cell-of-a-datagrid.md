---
title: "Postupy: Provedení vlastní akce na základě změn v buňce ovládacího prvku Windows Forms DataGridView"
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
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e1b34881b86d9962603118b93c9dc5d866794397
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a><span data-ttu-id="54020-102">Postupy: Provedení vlastní akce na základě změn v buňce ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="54020-102">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="54020-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek má určitý počet událostí můžete použít ke zjištění změny ve stavu <xref:System.Windows.Forms.DataGridView> buněk.</span><span class="sxs-lookup"><span data-stu-id="54020-103">The <xref:System.Windows.Forms.DataGridView> control has a number of events you can use to detect changes in the state of <xref:System.Windows.Forms.DataGridView> cells.</span></span> <span data-ttu-id="54020-104">Dva z nejčastěji používaných jsou <xref:System.Windows.Forms.DataGridView.CellValueChanged> a <xref:System.Windows.Forms.DataGridView.CellStateChanged> události.</span><span class="sxs-lookup"><span data-stu-id="54020-104">Two of the most commonly used are the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a><span data-ttu-id="54020-105">Ke zjištění změn v hodnoty buněk DataGridView</span><span class="sxs-lookup"><span data-stu-id="54020-105">To detect changes in the values of DataGridView cells</span></span>  
  
-   <span data-ttu-id="54020-106">Zápis obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellValueChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="54020-106">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellValueChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a><span data-ttu-id="54020-107">Ke zjištění změny ve stavu buněk DataGridView</span><span class="sxs-lookup"><span data-stu-id="54020-107">To detect changes in the states of DataGridView cells</span></span>  
  
-   <span data-ttu-id="54020-108">Zápis obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellStateChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="54020-108">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellStateChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="54020-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="54020-109">Compiling the Code</span></span>  
 <span data-ttu-id="54020-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="54020-110">This example requires:</span></span>  
  
-   <span data-ttu-id="54020-111">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="54020-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span> <span data-ttu-id="54020-112">Pro jazyk C# obslužné rutiny události musí být připojen k odpovídající události.</span><span class="sxs-lookup"><span data-stu-id="54020-112">For C#, the event handlers must be connected to the corresponding events.</span></span>  
  
-   <span data-ttu-id="54020-113">Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="54020-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54020-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="54020-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>  
 [<span data-ttu-id="54020-115">Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="54020-115">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 [<span data-ttu-id="54020-116">Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="54020-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
