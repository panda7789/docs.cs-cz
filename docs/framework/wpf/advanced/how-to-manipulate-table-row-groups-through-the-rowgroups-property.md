---
title: 'Postupy: Zpracování skupin řádků tabulky prostřednictvím vlastnosti RowGroups'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- row groups [WPF], manipulating through RowGroups property
- RowGroups property [WPF], manipulating row groups
- documents [WPF], manipulating row groups through RowGroups property
- properties [WPF], RowGroups [WPF], manipulating row groups
ms.assetid: ea61440f-08ae-44ed-b314-5716aaaae3ed
ms.openlocfilehash: 195920af64888bd3671b45befc0fe4cde463ae7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913561"
---
# <a name="how-to-manipulate-a-tables-row-groups-through-the-rowgroups-property"></a><span data-ttu-id="bc283-102">Postupy: Zpracování skupin řádků tabulky prostřednictvím vlastnosti RowGroups</span><span class="sxs-lookup"><span data-stu-id="bc283-102">How to: Manipulate a Table's Row Groups through the RowGroups Property</span></span>
<span data-ttu-id="bc283-103">Tento příklad ukazuje některé z nejběžnějších operací, které lze provádět na skupinách řádků tabulky prostřednictvím <xref:System.Windows.Documents.Table.RowGroups%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bc283-103">This example demonstrates some of the more common operations that can be performed on a table's row groups through the <xref:System.Windows.Documents.Table.RowGroups%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc283-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc283-104">Example</span></span>  
 <span data-ttu-id="bc283-105">Následující příklad vytvoří novou tabulku a poté pomocí <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> metody přidá sloupce do <xref:System.Windows.Documents.Table.RowGroups%2A> kolekce tabulky.</span><span class="sxs-lookup"><span data-stu-id="bc283-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.RowGroups%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a><span data-ttu-id="bc283-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc283-106">Example</span></span>  
 <span data-ttu-id="bc283-107">Následující příklad vloží nový <xref:System.Windows.Documents.TableRowGroup>.</span><span class="sxs-lookup"><span data-stu-id="bc283-107">The following example inserts a new <xref:System.Windows.Documents.TableRowGroup>.</span></span>  <span data-ttu-id="bc283-108">Nový sloupec je vložen na pozici indexu 0, takže se stane novou skupinou prvního řádku v tabulce.</span><span class="sxs-lookup"><span data-stu-id="bc283-108">The new column is inserted at index position 0, making it the new first row group in the table.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc283-109"><xref:System.Windows.Documents.TableRowGroupCollection> Kolekce používá standardní indexování založené na nule.</span><span class="sxs-lookup"><span data-stu-id="bc283-109">The <xref:System.Windows.Documents.TableRowGroupCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a><span data-ttu-id="bc283-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc283-110">Example</span></span>  
 <span data-ttu-id="bc283-111">Následující příklad přidá několik řádků do konkrétního <xref:System.Windows.Documents.TableRowGroup> (určeného indexem) v tabulce.</span><span class="sxs-lookup"><span data-stu-id="bc283-111">The following example adds several rows to a particular <xref:System.Windows.Documents.TableRowGroup> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a><span data-ttu-id="bc283-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc283-112">Example</span></span>  
 <span data-ttu-id="bc283-113">Následující příklad přistupuje k nějakým libovolným vlastnostem v řádcích v první skupině řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="bc283-113">The following example accesses some arbitrary properties on rows in the first row group in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a><span data-ttu-id="bc283-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc283-114">Example</span></span>  
 <span data-ttu-id="bc283-115">Následující příklad přidá několik buněk do konkrétního <xref:System.Windows.Documents.TableRow> (určeného indexem) v tabulce.</span><span class="sxs-lookup"><span data-stu-id="bc283-115">The following example adds several cells to a particular <xref:System.Windows.Documents.TableRow> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a><span data-ttu-id="bc283-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc283-116">Example</span></span>  
 <span data-ttu-id="bc283-117">Následující příklad přistupuje k některým metodám a vlastnostem v buňkách prvního řádku v první skupině řádků.</span><span class="sxs-lookup"><span data-stu-id="bc283-117">The following example access some arbitrary methods and properties on cells in the first row in the first row group.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a><span data-ttu-id="bc283-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc283-118">Example</span></span>  
 <span data-ttu-id="bc283-119">Následující příklad vrátí počet <xref:System.Windows.Documents.TableRowGroup> prvků hostovaných tabulkou.</span><span class="sxs-lookup"><span data-stu-id="bc283-119">The following example returns the number of <xref:System.Windows.Documents.TableRowGroup> elements hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a><span data-ttu-id="bc283-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc283-120">Example</span></span>  
 <span data-ttu-id="bc283-121">Následující příklad odebere určitou skupinu řádků podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="bc283-121">The following example removes a particular row group by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a><span data-ttu-id="bc283-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc283-122">Example</span></span>  
 <span data-ttu-id="bc283-123">Následující příklad odebere určitou skupinu řádků podle indexu.</span><span class="sxs-lookup"><span data-stu-id="bc283-123">The following example removes a particular row group by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a><span data-ttu-id="bc283-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc283-124">Example</span></span>  
 <span data-ttu-id="bc283-125">Následující příklad odebere všechny skupiny řádků z kolekce skupin řádků tabulky.</span><span class="sxs-lookup"><span data-stu-id="bc283-125">The following example removes all row groups from the table's row groups collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="bc283-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc283-126">See also</span></span>

- [<span data-ttu-id="bc283-127">Postupy: Manipulace s elementy obsahu toku prostřednictvím vlastnosti Inlines</span><span class="sxs-lookup"><span data-stu-id="bc283-127">How-to: Manipulate Flow Content Elements through the Inlines Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="bc283-128">Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks</span><span class="sxs-lookup"><span data-stu-id="bc283-128">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="bc283-129">Zpracování sloupců tabulky prostřednictvím vlastnosti Columns</span><span class="sxs-lookup"><span data-stu-id="bc283-129">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
