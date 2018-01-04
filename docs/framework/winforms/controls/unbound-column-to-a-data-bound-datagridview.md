---
title: "Postupy: Přidání nepřipojeného sloupce do daty připojeného ovládacího prvku Windows Forms DataGridView"
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
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2861db5434e58bd14bf82604252fc0060d9b38d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="e2db4-102">Postupy: Přidání nepřipojeného sloupce do daty připojeného ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e2db4-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e2db4-103">Data můžete zobrazit v <xref:System.Windows.Forms.DataGridView> ovládací prvek bude obvykle pocházet ze zdroje dat určitého druhu, ale můžete chtít zobrazit sloupce dat, které nepochází ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="e2db4-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="e2db4-104">Tento druh sloupec se nazývá nepřipojeného sloupce.</span><span class="sxs-lookup"><span data-stu-id="e2db4-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="e2db4-105">Nevázaných sloupců mohou mít mnoho forem.</span><span class="sxs-lookup"><span data-stu-id="e2db4-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="e2db4-106">Často se používají k poskytování přístupu k podrobnosti o data v řádku.</span><span class="sxs-lookup"><span data-stu-id="e2db4-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="e2db4-107">Následující příklad kódu ukazuje, jak vytvořit nepřipojeného sloupce z **podrobnosti** tlačítka zobrazíte podřízené tabulky související s konkrétního řádku v nadřazené tabulce při implementaci scénáři a podrobností.</span><span class="sxs-lookup"><span data-stu-id="e2db4-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="e2db4-108">Reagovat na kliknutí na tlačítko, implementovat <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> obslužné rutiny události, které zobrazí formulář obsahující podřízenou tabulku.</span><span class="sxs-lookup"><span data-stu-id="e2db4-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="e2db4-109">Není poskytována podpora pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e2db4-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="e2db4-110">Viz také [postupy: Přidání a odebrání sloupců v Windows Forms DataGridView – ovládací prvek pomocí návrháře](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e2db4-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2db4-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2db4-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e2db4-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e2db4-112">Compiling the Code</span></span>  
 <span data-ttu-id="e2db4-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e2db4-113">This example requires:</span></span>  
  
-   <span data-ttu-id="e2db4-114">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="e2db4-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="e2db4-115">Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="e2db4-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2db4-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2db4-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="e2db4-117">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e2db4-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="e2db4-118">Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e2db4-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
