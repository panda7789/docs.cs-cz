---
title: Přidání nevázaného sloupce do ovládacího prvku DataGridView vázaného na data
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 807bbc121f33c35d70068571e76637c078ecb3da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747061"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="b1cd8-102">Postupy: Přidání nepřipojeného sloupce do daty připojeného ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b1cd8-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b1cd8-103">Data, která zobrazíte v ovládacím prvku <xref:System.Windows.Forms.DataGridView>, budou normálně pocházet ze zdroje dat nějakého druhu, ale možná budete chtít zobrazit sloupec dat, která nepochází ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="b1cd8-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="b1cd8-104">Tento druh sloupce se nazývá nevázaný sloupec.</span><span class="sxs-lookup"><span data-stu-id="b1cd8-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="b1cd8-105">Nevázané sloupce mohou mít mnoho forem.</span><span class="sxs-lookup"><span data-stu-id="b1cd8-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="b1cd8-106">Často se používají k poskytnutí přístupu k podrobnostem datového řádku.</span><span class="sxs-lookup"><span data-stu-id="b1cd8-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="b1cd8-107">Následující příklad kódu ukazuje, jak vytvořit nevázaný sloupec tlačítek **podrobností** k zobrazení podřízené tabulky související s konkrétním řádkem v nadřazené tabulce při implementaci scénáře hlavní/podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="b1cd8-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="b1cd8-108">Chcete-li reagovat na kliknutí na tlačítko, Implementujte obslužnou rutinu události <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>, která zobrazí formulář obsahující podřízenou tabulku.</span><span class="sxs-lookup"><span data-stu-id="b1cd8-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="b1cd8-109">Pro tuto úlohu se v aplikaci Visual Studio podporuje.</span><span class="sxs-lookup"><span data-stu-id="b1cd8-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="b1cd8-110">Viz také [Postupy: Přidání a odebrání sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="b1cd8-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1cd8-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1cd8-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b1cd8-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b1cd8-112">Compiling the Code</span></span>  
 <span data-ttu-id="b1cd8-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b1cd8-113">This example requires:</span></span>  
  
- <span data-ttu-id="b1cd8-114"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="b1cd8-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="b1cd8-115">Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="b1cd8-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1cd8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1cd8-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="b1cd8-117">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b1cd8-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b1cd8-118">Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b1cd8-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
