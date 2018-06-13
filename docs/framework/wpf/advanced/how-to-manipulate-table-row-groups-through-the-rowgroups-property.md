---
title: 'Postupy: manipulace s tabulku&#39;skupin řádků s prostřednictvím vlastnosti RowGroups'
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
ms.openlocfilehash: 8cdf3b74fa5bf5a566c541ba035a1c7da7dd6949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545162"
---
# <a name="how-to-manipulate-a-table39s-row-groups-through-the-rowgroups-property"></a><span data-ttu-id="fb3b0-102">Postupy: manipulace s tabulku&#39;skupin řádků s prostřednictvím vlastnosti RowGroups</span><span class="sxs-lookup"><span data-stu-id="fb3b0-102">How to: Manipulate a Table&#39;s Row Groups through the RowGroups Property</span></span>
<span data-ttu-id="fb3b0-103">Tento příklad ukazuje některé z nejčastěji operací, které lze provést na skupiny řádků tabulky prostřednictvím <xref:System.Windows.Documents.Table.RowGroups%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-103">This example demonstrates some of the more common operations that can be performed on a table's row groups through the <xref:System.Windows.Documents.Table.RowGroups%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb3b0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb3b0-104">Example</span></span>  
 <span data-ttu-id="fb3b0-105">Následující příklad vytvoří novou tabulku a potom pomocí <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> metody přidat sloupce do tabulky <xref:System.Windows.Documents.Table.RowGroups%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.RowGroups%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a><span data-ttu-id="fb3b0-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb3b0-106">Example</span></span>  
 <span data-ttu-id="fb3b0-107">Následující příklad vloží novou <xref:System.Windows.Documents.TableRowGroup>.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-107">The following example inserts a new <xref:System.Windows.Documents.TableRowGroup>.</span></span>  <span data-ttu-id="fb3b0-108">Je na pozici indexu 0, což nový první řádek vložit nový sloupec v tabulce.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-108">The new column is inserted at index position 0, making it the new first row group in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb3b0-109"><xref:System.Windows.Documents.TableRowGroupCollection> Kolekce používá standardní indexování od nuly.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-109">The <xref:System.Windows.Documents.TableRowGroupCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a><span data-ttu-id="fb3b0-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb3b0-110">Example</span></span>  
 <span data-ttu-id="fb3b0-111">Následující příklad přidá několik řádků ke konkrétní <xref:System.Windows.Documents.TableRowGroup> (zadán indexem) v tabulce.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-111">The following example adds several rows to a particular <xref:System.Windows.Documents.TableRowGroup> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a><span data-ttu-id="fb3b0-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb3b0-112">Example</span></span>  
 <span data-ttu-id="fb3b0-113">Následující příklad používá některé libovolné vlastnosti v řádcích ve skupině první řádek v tabulce.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-113">The following example accesses some arbitrary properties on rows in the first row group in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a><span data-ttu-id="fb3b0-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb3b0-114">Example</span></span>  
 <span data-ttu-id="fb3b0-115">Následující příklad přidá několika buněk ke konkrétní <xref:System.Windows.Documents.TableRow> (zadán indexem) v tabulce.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-115">The following example adds several cells to a particular <xref:System.Windows.Documents.TableRow> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a><span data-ttu-id="fb3b0-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb3b0-116">Example</span></span>  
 <span data-ttu-id="fb3b0-117">Následující příklad přístup některé libovolné metody a vlastnosti buněk v první řádek v první skupiny řádků.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-117">The following example access some arbitrary methods and properties on cells in the first row in the first row group.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a><span data-ttu-id="fb3b0-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb3b0-118">Example</span></span>  
 <span data-ttu-id="fb3b0-119">Následující příklad vrátí počet <xref:System.Windows.Documents.TableRowGroup> elementy, které jsou hostované v tabulce.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-119">The following example returns the number of <xref:System.Windows.Documents.TableRowGroup> elements hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a><span data-ttu-id="fb3b0-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb3b0-120">Example</span></span>  
 <span data-ttu-id="fb3b0-121">Následující příklad odebere skupinu konkrétního řádku odkazem.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-121">The following example removes a particular row group by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a><span data-ttu-id="fb3b0-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb3b0-122">Example</span></span>  
 <span data-ttu-id="fb3b0-123">Následující příklad odebere skupinu konkrétního řádku index.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-123">The following example removes a particular row group by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a><span data-ttu-id="fb3b0-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb3b0-124">Example</span></span>  
 <span data-ttu-id="fb3b0-125">Následující příklad odebere všechny skupiny řádků z kolekce skupin řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="fb3b0-125">The following example removes all row groups from the table's row groups collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="fb3b0-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb3b0-126">See Also</span></span>  
 [<span data-ttu-id="fb3b0-127">Postupy: Manipulace s prvky toku obsahu prostřednictvím vlastnosti Inlines</span><span class="sxs-lookup"><span data-stu-id="fb3b0-127">How-to: Manipulate Flow Content Elements through the Inlines Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="fb3b0-128">Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks</span><span class="sxs-lookup"><span data-stu-id="fb3b0-128">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [<span data-ttu-id="fb3b0-129">Zpracování sloupců tabulky prostřednictvím vlastnosti Columns</span><span class="sxs-lookup"><span data-stu-id="fb3b0-129">Manipulate a Table's Columns through the Columns Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)
