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
ms.openlocfilehash: ad6e704b64e3f25f456b98691dfe12c13f8440a2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713295"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6fda3-102">Postupy: Získání vybraných buněk, řádků a sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6fda3-102">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6fda3-103">Můžete získat vybraných buněk, řádků nebo sloupců z <xref:System.Windows.Forms.DataGridView> ovládacího prvku pomocí odpovídajících vlastností: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, a <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="6fda3-103">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="6fda3-104">V následujících postupech se získání vybraných buněk a zobrazí jejich řádků a sloupců indexy <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="6fda3-104">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="6fda3-105">K získání vybraných buněk v ovládacím prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="6fda3-105">To get the selected cells in a DataGridView control</span></span>  
  
-   <span data-ttu-id="6fda3-106">Použití <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6fda3-106">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6fda3-107">Použití <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metody, aby nedocházelo k zobrazení potenciálně velký počet buněk.</span><span class="sxs-lookup"><span data-stu-id="6fda3-107">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="6fda3-108">Chcete-li získat vybraných řádků v ovládacím prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="6fda3-108">To get the selected rows in a DataGridView control</span></span>  
  
-   <span data-ttu-id="6fda3-109">Použití <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6fda3-109">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="6fda3-110">Pokud chcete povolit uživatelům výběr řádků, je nutné nastavit <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="6fda3-110">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="6fda3-111">Chcete-li získat z vybraných sloupců v ovládacím prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="6fda3-111">To get the selected columns in a DataGridView control</span></span>  
  
-   <span data-ttu-id="6fda3-112">Použití <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6fda3-112">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="6fda3-113">Pokud chcete povolit uživatelům výběr sloupce, je nutné nastavit <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="6fda3-113">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6fda3-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6fda3-114">Compiling the Code</span></span>  
 <span data-ttu-id="6fda3-115">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="6fda3-115">This example requires:</span></span>  
  
-   <span data-ttu-id="6fda3-116"><xref:System.Windows.Forms.Button> ovládací prvky s názvem `selectedCellsButton`, `selectedRowsButton`, a `selectedColumnsButton`, každý s obslužnými rutinami pro <xref:System.Windows.Forms.Control.Click> připojené události.</span><span class="sxs-lookup"><span data-stu-id="6fda3-116"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
-   <span data-ttu-id="6fda3-117">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="6fda3-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="6fda3-118">Odkazy <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Text?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="6fda3-118">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6fda3-119">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="6fda3-119">Robust Programming</span></span>  
 <span data-ttu-id="6fda3-120">Kolekce je popsáno v tomto tématu neprovádějte efektivně vybrání velký počet buněk, řádků nebo sloupců.</span><span class="sxs-lookup"><span data-stu-id="6fda3-120">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="6fda3-121">Další informace o použití těchto kolekcí s velkými objemy dat, naleznete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="6fda3-121">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fda3-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fda3-122">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="6fda3-123">Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="6fda3-123">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
