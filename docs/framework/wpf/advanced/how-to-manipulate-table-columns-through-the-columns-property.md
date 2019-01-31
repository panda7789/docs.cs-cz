---
title: 'Postupy: Práce se sloupci tabulky prostřednictvím vlastnosti Columns'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], manipulating table columns
- properties [WPF], Columns [WPF], manipulating table columns
- tables [WPF], manipulating columns
- Columns property [WPF]
ms.assetid: 3f8884f4-7e1f-456b-be06-fbd3cf469bf3
ms.openlocfilehash: e3327b59cb8c387cb554206d1b17c2cd7002ef80
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258094"
---
# <a name="how-to-manipulate-a-tables-columns-through-the-columns-property"></a><span data-ttu-id="2458f-102">Postupy: Práce se sloupci tabulky prostřednictvím vlastnosti Columns</span><span class="sxs-lookup"><span data-stu-id="2458f-102">How to: Manipulate a Table's Columns through the Columns Property</span></span>
<span data-ttu-id="2458f-103">Tento příklad ukazuje některé běžné operace, které lze provést na sloupci tabulky prostřednictvím <xref:System.Windows.Documents.Table.Columns%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2458f-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2458f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2458f-104">Example</span></span>  
 <span data-ttu-id="2458f-105">Následující příklad vytvoří novou tabulku a poté použije <xref:System.Windows.Documents.TableColumnCollection.Add%2A> metodu pro přidání sloupce do tabulky <xref:System.Windows.Documents.Table.Columns%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="2458f-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="2458f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="2458f-106">Example</span></span>  
 <span data-ttu-id="2458f-107">V následujícím příkladu vloží nový <xref:System.Windows.Documents.TableColumn>.</span><span class="sxs-lookup"><span data-stu-id="2458f-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="2458f-108">Nový sloupec je vložené na pozici indexu 0, takže nové první sloupec v tabulce.</span><span class="sxs-lookup"><span data-stu-id="2458f-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2458f-109"><xref:System.Windows.Documents.TableColumnCollection> Kolekce používá standardní indexování od nuly.</span><span class="sxs-lookup"><span data-stu-id="2458f-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="2458f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="2458f-110">Example</span></span>  
 <span data-ttu-id="2458f-111">Následující příklad přistupuje k některé libovolné vlastnosti pro sloupce v <xref:System.Windows.Documents.TableColumnCollection> kolekce odkazuje na konkrétní sloupce podle indexu.</span><span class="sxs-lookup"><span data-stu-id="2458f-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="2458f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="2458f-112">Example</span></span>  
 <span data-ttu-id="2458f-113">Následující příklad získá počet sloupců, které jsou momentálně hostované v tabulce.</span><span class="sxs-lookup"><span data-stu-id="2458f-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="2458f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="2458f-114">Example</span></span>  
 <span data-ttu-id="2458f-115">Následující příklad odebere konkrétního sloupce podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="2458f-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="2458f-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="2458f-116">Example</span></span>  
 <span data-ttu-id="2458f-117">Následující příklad odebere konkrétního sloupce podle indexu.</span><span class="sxs-lookup"><span data-stu-id="2458f-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="2458f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="2458f-118">Example</span></span>  
 <span data-ttu-id="2458f-119">Následující příklad odebere všechny sloupce z kolekce sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="2458f-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="2458f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2458f-120">See also</span></span>
- [<span data-ttu-id="2458f-121">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="2458f-121">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
- [<span data-ttu-id="2458f-122">Definice tabulky pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="2458f-122">Define a Table with XAML</span></span>](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="2458f-123">Sestavení tabulky z programu</span><span class="sxs-lookup"><span data-stu-id="2458f-123">Build a Table Programmatically</span></span>](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)
- [<span data-ttu-id="2458f-124">Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups</span><span class="sxs-lookup"><span data-stu-id="2458f-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="2458f-125">Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks</span><span class="sxs-lookup"><span data-stu-id="2458f-125">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="2458f-126">Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups</span><span class="sxs-lookup"><span data-stu-id="2458f-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
