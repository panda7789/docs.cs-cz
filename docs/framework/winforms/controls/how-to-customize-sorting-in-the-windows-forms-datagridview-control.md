---
title: Přizpůsobení řazení v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 20f581b2df6fd172a0a1998aed60c56b0306f2eb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743176"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ba3c6-102">Postupy: Přizpůsobení třídění v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ba3c6-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ba3c6-103">Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje automatické řazení, ale v závislosti na vašich potřebách možná budete muset přizpůsobit operace řazení.</span><span class="sxs-lookup"><span data-stu-id="ba3c6-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="ba3c6-104">Programové řazení můžete například použít k vytvoření alternativního uživatelského rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="ba3c6-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="ba3c6-105">Alternativně můžete zpracovat událost <xref:System.Windows.Forms.DataGridView.SortCompare> nebo volat přetížení `Sort(IComparer)` metody <xref:System.Windows.Forms.DataGridView.Sort%2A> pro větší flexibilitu řazení, jako je například řazení více sloupců.</span><span class="sxs-lookup"><span data-stu-id="ba3c6-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="ba3c6-106">Následující příklady kódu ukazují tyto tři přístupy k vlastnímu řazení.</span><span class="sxs-lookup"><span data-stu-id="ba3c6-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="ba3c6-107">Další informace naleznete v tématu [režimy řazení sloupců v ovládacím prvku DataGridView model Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="ba3c6-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="ba3c6-108">Programové řazení</span><span class="sxs-lookup"><span data-stu-id="ba3c6-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="ba3c6-109">Následující příklad kódu ukazuje programové řazení pomocí vlastností <xref:System.Windows.Forms.DataGridView.SortOrder%2A> a <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> k určení směru řazení a vlastnost <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> k ručnímu nastavení glyfu řazení.</span><span class="sxs-lookup"><span data-stu-id="ba3c6-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="ba3c6-110">`Sort(DataGridViewColumn,ListSortDirection)` přetížení metody <xref:System.Windows.Forms.DataGridView.Sort%2A> slouží k řazení dat pouze do jednoho sloupce.</span><span class="sxs-lookup"><span data-stu-id="ba3c6-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="ba3c6-111">Vlastní řazení pomocí události SortCompare</span><span class="sxs-lookup"><span data-stu-id="ba3c6-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="ba3c6-112">Následující příklad kódu ukazuje vlastní řazení pomocí <xref:System.Windows.Forms.DataGridView.SortCompare> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ba3c6-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="ba3c6-113">Vybraná <xref:System.Windows.Forms.DataGridViewColumn> je seřazená a pokud ve sloupci existují duplicitní hodnoty, použije se k určení konečného pořadí sloupec ID.</span><span class="sxs-lookup"><span data-stu-id="ba3c6-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="ba3c6-114">Vlastní řazení pomocí rozhraní IComparer</span><span class="sxs-lookup"><span data-stu-id="ba3c6-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="ba3c6-115">Následující příklad kódu ukazuje vlastní řazení pomocí `Sort(IComparer)` přetížení metody <xref:System.Windows.Forms.DataGridView.Sort%2A>, která přebírá implementaci rozhraní <xref:System.Collections.IComparer> k provedení řazení ve více sloupcích.</span><span class="sxs-lookup"><span data-stu-id="ba3c6-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ba3c6-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ba3c6-116">Compiling the Code</span></span>  
 <span data-ttu-id="ba3c6-117">Tyto příklady vyžadují:</span><span class="sxs-lookup"><span data-stu-id="ba3c6-117">These examples require:</span></span>  
  
- <span data-ttu-id="ba3c6-118">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="ba3c6-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba3c6-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba3c6-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="ba3c6-120">Řazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ba3c6-120">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ba3c6-121">Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ba3c6-121">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ba3c6-122">Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ba3c6-122">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)
