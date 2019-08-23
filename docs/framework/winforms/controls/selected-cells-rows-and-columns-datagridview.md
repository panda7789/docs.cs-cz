---
title: 'Postupy: Získání vybraných buněk, řádků a sloupců v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 25b3ed50081add77b9f522ca8e597f2b3306cb2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960518"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1480a-102">Postupy: Získání vybraných buněk, řádků a sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1480a-102">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1480a-103">Vybrané buňky, řádky nebo <xref:System.Windows.Forms.DataGridView> sloupce můžete získat z ovládacího prvku pomocí odpovídajících vlastností: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>a <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="1480a-103">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="1480a-104">V následujících postupech zobrazíte vybrané buňky a zobrazíte jejich indexy řádků a sloupců v <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="1480a-104">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="1480a-105">Získání vybraných buněk v ovládacím prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="1480a-105">To get the selected cells in a DataGridView control</span></span>  
  
- <span data-ttu-id="1480a-106"><xref:System.Windows.Forms.DataGridView.SelectedCells%2A> Použijte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1480a-106">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1480a-107"><xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> Použijte metodu k zamezení zobrazení potenciálně velkého počtu buněk.</span><span class="sxs-lookup"><span data-stu-id="1480a-107">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="1480a-108">Získání vybraných řádků v ovládacím prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="1480a-108">To get the selected rows in a DataGridView control</span></span>  
  
- <span data-ttu-id="1480a-109"><xref:System.Windows.Forms.DataGridView.SelectedRows%2A> Použijte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1480a-109">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="1480a-110">Chcete-li uživatelům umožnit výběr řádků, je nutné nastavit <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> vlastnost na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="1480a-110">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="1480a-111">Získání vybraných sloupců v ovládacím prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="1480a-111">To get the selected columns in a DataGridView control</span></span>  
  
- <span data-ttu-id="1480a-112"><xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> Použijte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1480a-112">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="1480a-113">Chcete-li uživatelům umožnit výběr sloupců, je nutné nastavit <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> vlastnost na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="1480a-113">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1480a-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1480a-114">Compiling the Code</span></span>  
 <span data-ttu-id="1480a-115">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1480a-115">This example requires:</span></span>  
  
- <span data-ttu-id="1480a-116"><xref:System.Windows.Forms.Button>ovládací prvky `selectedCellsButton`s `selectedRowsButton`názvem, `selectedColumnsButton`a, každý s obslužnými <xref:System.Windows.Forms.Control.Click> rutinami pro připojenou událost.</span><span class="sxs-lookup"><span data-stu-id="1480a-116"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
- <span data-ttu-id="1480a-117">Ovládací prvek s `dataGridView1`názvem. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="1480a-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="1480a-118">Odkazy na <xref:System?displayProperty=nameWithType>sestavení, <xref:System.Windows.Forms?displayProperty=nameWithType>a. <xref:System.Text?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1480a-118">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1480a-119">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1480a-119">Robust Programming</span></span>  
 <span data-ttu-id="1480a-120">Kolekce popsané v tomto tématu neprovádějte efektivně, pokud je vybrán velký počet buněk, řádků nebo sloupců.</span><span class="sxs-lookup"><span data-stu-id="1480a-120">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="1480a-121">Další informace o použití těchto kolekcí s velkým objemem dat naleznete v tématu [osvědčené postupy pro škálování ovládacího prvku DataGridView model Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1480a-121">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1480a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1480a-122">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="1480a-123">Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1480a-123">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
