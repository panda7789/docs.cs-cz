---
title: 'Postupy: Přidání nepřipojeného sloupce do ovládacího prvku Windows Forms DataGridView s datovou vazbou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 40308f7e8cc12dcff5b7d4393645f6a9007cc2b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009198"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="b9156-102">Postupy: Přidání nepřipojeného sloupce do ovládacího prvku Windows Forms DataGridView s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="b9156-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b9156-103">Data můžete zobrazit v <xref:System.Windows.Forms.DataGridView> ovládací prvek bude obvykle pocházejí ze zdroje dat určitého druhu, ale můžete chtít zobrazit sloupce dat, které nepochází ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="b9156-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="b9156-104">Tento typ sloupce se nazývá nepřipojeného sloupce.</span><span class="sxs-lookup"><span data-stu-id="b9156-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="b9156-105">Nevázaného sloupce mohou mít mnoho forem.</span><span class="sxs-lookup"><span data-stu-id="b9156-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="b9156-106">Často se používají k poskytnutí přístupu podrobné informace o datovém řádku.</span><span class="sxs-lookup"><span data-stu-id="b9156-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="b9156-107">Následující příklad kódu ukazuje, jak vytvořit nepřipojeného sloupce z **podrobnosti** tlačítka zobrazíte podřízené tabulky související s konkrétního řádku v nadřazené tabulce, Pokud implementujete scénář záznamů master/detail.</span><span class="sxs-lookup"><span data-stu-id="b9156-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="b9156-108">Reakce na kliknutí na tlačítko, implementovat <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> obslužná rutina události, které zobrazí formulář obsahující podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="b9156-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="b9156-109">Není poskytována podpora pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b9156-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="b9156-110">Viz také [jak: Přidat a odebrat sloupce v Windows Forms DataGridView pomocí návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="b9156-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9156-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9156-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9156-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b9156-112">Compiling the Code</span></span>  
 <span data-ttu-id="b9156-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b9156-113">This example requires:</span></span>  
  
- <span data-ttu-id="b9156-114">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="b9156-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="b9156-115">Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="b9156-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9156-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9156-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="b9156-117">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b9156-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b9156-118">Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b9156-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
