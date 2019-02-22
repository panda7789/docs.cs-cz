---
title: 'Postupy: Přizpůsobení třídění v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 2eb7b66b52770f8641cc56adb1829ba590ba5874
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584184"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e3697-102">Postupy: Přizpůsobení třídění v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e3697-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e3697-103"><xref:System.Windows.Forms.DataGridView> Řízení poskytuje automatické řazení, ale v závislosti na potřebách, možná budete muset přizpůsobit operace řazení.</span><span class="sxs-lookup"><span data-stu-id="e3697-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="e3697-104">Například můžete řazení prostřednictvím kódu programu vytvořit alternativní uživatelské rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="e3697-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="e3697-105">Alternativně můžete zpracovávat <xref:System.Windows.Forms.DataGridView.SortCompare> události nebo volání `Sort(IComparer)` přetížení <xref:System.Windows.Forms.DataGridView.Sort%2A> metodu pro vyšší flexibilitu řazení, jako je například řazení více sloupců.</span><span class="sxs-lookup"><span data-stu-id="e3697-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="e3697-106">Následující příklady kódu ukazují tyto tři přístupy k vlastní řazení.</span><span class="sxs-lookup"><span data-stu-id="e3697-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="e3697-107">Další informace najdete v tématu [režimy třídění sloupce v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e3697-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="e3697-108">Řazení prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="e3697-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="e3697-109">Následující příklad kódu ukazuje programová řazení pomocí <xref:System.Windows.Forms.DataGridView.SortOrder%2A> a <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> vlastnosti k určení směru řazení a <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> vlastnost piktogram setřídit nastavit ručně.</span><span class="sxs-lookup"><span data-stu-id="e3697-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="e3697-110">`Sort(DataGridViewColumn,ListSortDirection)` Přetížení <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda se používá k řazení dat pouze na jeden sloupec.</span><span class="sxs-lookup"><span data-stu-id="e3697-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="e3697-111">Vlastní řazení pomocí SortCompare události</span><span class="sxs-lookup"><span data-stu-id="e3697-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="e3697-112">Následující příklad kódu ukazuje vlastní řazení pomocí <xref:System.Windows.Forms.DataGridView.SortCompare> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="e3697-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="e3697-113">Vybrané <xref:System.Windows.Forms.DataGridViewColumn> je seřazený a, pokud existují duplicitní hodnoty ve sloupci, ID sloupce se používá k určení konečnou verzi objednávky.</span><span class="sxs-lookup"><span data-stu-id="e3697-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="e3697-114">Vlastní řazení pomocí rozhraní IComparer</span><span class="sxs-lookup"><span data-stu-id="e3697-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="e3697-115">Následující příklad kódu ukazuje vlastní řazení pomocí `Sort(IComparer)` přetížení <xref:System.Windows.Forms.DataGridView.Sort%2A> metodu, která přebírá implementaci <xref:System.Collections.IComparer> rozhraní k provedení řazení více sloupců.</span><span class="sxs-lookup"><span data-stu-id="e3697-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e3697-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e3697-116">Compiling the Code</span></span>  
 <span data-ttu-id="e3697-117">Tyto příklady vyžadují:</span><span class="sxs-lookup"><span data-stu-id="e3697-117">These examples require:</span></span>  
  
-   <span data-ttu-id="e3697-118">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e3697-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e3697-119">Informace o vytváření těchto příkladech z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e3697-119">For information about building these examples from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e3697-120">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="e3697-120">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3697-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3697-121">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="e3697-122">Řazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e3697-122">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e3697-123">Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e3697-123">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e3697-124">Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e3697-124">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)
