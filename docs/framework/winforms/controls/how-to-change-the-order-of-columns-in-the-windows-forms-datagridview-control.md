---
title: 'Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: 75362a2623cfe685f38259b9e581b593b2bd8d17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530611"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="10657-102">Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="10657-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="10657-103">Při použití <xref:System.Windows.Forms.DataGridView> k zobrazení dat ze zdroje dat, sloupce ve zdroji dat schématu někdy nejsou uvedeny v pořadí, které chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="10657-103">When you use a <xref:System.Windows.Forms.DataGridView> to display data from a data source, the columns in the data source's schema sometimes do not appear in the order you would like to display them.</span></span> <span data-ttu-id="10657-104">Zobrazit pořadí sloupců můžete změnit pomocí <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> vlastnost <xref:System.Windows.Forms.DataGridViewColumn> třídy.</span><span class="sxs-lookup"><span data-stu-id="10657-104">You can change the displayed order of the columns by using the <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> property of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <span data-ttu-id="10657-105">Následující příklad kódu přemístí některé sloupce automaticky generuje při vytváření vazby pro tabulku zákazníků v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="10657-105">The following code example repositions some of the columns automatically generated when binding to the Customers table in the Northwind sample database.</span></span> <span data-ttu-id="10657-106">Další informace o tom, jak vytvořit vazbu <xref:System.Windows.Forms.DataGridView> řízení do databázové tabulky, najdete v části [postupy: vytvoření vazby dat ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="10657-106">For more information about how to bind the <xref:System.Windows.Forms.DataGridView> control to a database table, see [How to: Bind Data to the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="10657-107">Není poskytována podpora pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="10657-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="10657-108">Viz také [postupy: Změna pořadí sloupců v Windows Forms DataGridView – ovládací prvek pomocí návrháře](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="10657-108">Also see [How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="10657-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="10657-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="10657-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="10657-110">Compiling the Code</span></span>  
 <span data-ttu-id="10657-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="10657-111">This example requires:</span></span>  
  
-   <span data-ttu-id="10657-112">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `customersDataGridView` , je vázán k tabulce s názvy označeného sloupce, jako `Customers` tabulky v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="10657-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView` that is bound to a table with the indicated column names, such as the `Customers` table in the Northwind sample database.</span></span>  
  
-   <span data-ttu-id="10657-113">Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, a <xref:System.Xml?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="10657-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10657-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="10657-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="10657-115">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="10657-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="10657-116">Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="10657-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)
