---
title: 'Postupy: manipulace s tabulku&#39;sloupce s prostřednictvím vlastnosti sloupce'
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
ms.openlocfilehash: 916764c621738ddc651580f1232e1f579a17e6f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545295"
---
# <a name="how-to-manipulate-a-table39s-columns-through-the-columns-property"></a><span data-ttu-id="6b9ed-102">Postupy: manipulace s tabulku&#39;sloupce s prostřednictvím vlastnosti sloupce</span><span class="sxs-lookup"><span data-stu-id="6b9ed-102">How to: Manipulate a Table&#39;s Columns through the Columns Property</span></span>
<span data-ttu-id="6b9ed-103">Tento příklad ukazuje některé z nejčastěji operací, které lze provést na sloupce tabulky prostřednictvím <xref:System.Windows.Documents.Table.Columns%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6b9ed-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b9ed-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b9ed-104">Example</span></span>  
 <span data-ttu-id="6b9ed-105">Následující příklad vytvoří novou tabulku a potom pomocí <xref:System.Windows.Documents.TableColumnCollection.Add%2A> metody přidat sloupce do tabulky <xref:System.Windows.Documents.Table.Columns%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="6b9ed-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="6b9ed-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b9ed-106">Example</span></span>  
 <span data-ttu-id="6b9ed-107">Následující příklad vloží novou <xref:System.Windows.Documents.TableColumn>.</span><span class="sxs-lookup"><span data-stu-id="6b9ed-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="6b9ed-108">Nový sloupec je vložen na pozici indexu 0, což nový první sloupec v tabulce.</span><span class="sxs-lookup"><span data-stu-id="6b9ed-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b9ed-109"><xref:System.Windows.Documents.TableColumnCollection> Kolekce používá standardní indexování od nuly.</span><span class="sxs-lookup"><span data-stu-id="6b9ed-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="6b9ed-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b9ed-110">Example</span></span>  
 <span data-ttu-id="6b9ed-111">Následující příklad používá některé libovolné vlastnosti na sloupce ve <xref:System.Windows.Documents.TableColumnCollection> kolekce, která odkazuje na konkrétní sloupce podle indexu.</span><span class="sxs-lookup"><span data-stu-id="6b9ed-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="6b9ed-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b9ed-112">Example</span></span>  
 <span data-ttu-id="6b9ed-113">Následující příklad získá počet sloupců, které jsou aktuálně hostované v tabulce.</span><span class="sxs-lookup"><span data-stu-id="6b9ed-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="6b9ed-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b9ed-114">Example</span></span>  
 <span data-ttu-id="6b9ed-115">Následující příklad odebere konkrétní sloupec odkazem.</span><span class="sxs-lookup"><span data-stu-id="6b9ed-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="6b9ed-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b9ed-116">Example</span></span>  
 <span data-ttu-id="6b9ed-117">Následující příklad odebere konkrétní sloupec podle indexu.</span><span class="sxs-lookup"><span data-stu-id="6b9ed-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="6b9ed-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b9ed-118">Example</span></span>  
 <span data-ttu-id="6b9ed-119">Následující příklad odebere všechny sloupce z kolekce sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="6b9ed-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="6b9ed-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b9ed-120">See Also</span></span>  
 [<span data-ttu-id="6b9ed-121">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="6b9ed-121">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [<span data-ttu-id="6b9ed-122">Definice tabulky pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="6b9ed-122">Define a Table with XAML</span></span>](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [<span data-ttu-id="6b9ed-123">Sestavení tabulky z programu</span><span class="sxs-lookup"><span data-stu-id="6b9ed-123">Build a Table Programmatically</span></span>](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)  
 [<span data-ttu-id="6b9ed-124">Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups</span><span class="sxs-lookup"><span data-stu-id="6b9ed-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="6b9ed-125">Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks</span><span class="sxs-lookup"><span data-stu-id="6b9ed-125">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [<span data-ttu-id="6b9ed-126">Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups</span><span class="sxs-lookup"><span data-stu-id="6b9ed-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
