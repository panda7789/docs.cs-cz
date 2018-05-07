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
---
# <a name="how-to-manipulate-a-table39s-columns-through-the-columns-property"></a>Postupy: manipulace s tabulku&#39;sloupce s prostřednictvím vlastnosti sloupce
Tento příklad ukazuje některé z nejčastěji operací, které lze provést na sloupce tabulky prostřednictvím <xref:System.Windows.Documents.Table.Columns%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou tabulku a potom pomocí <xref:System.Windows.Documents.TableColumnCollection.Add%2A> metody přidat sloupce do tabulky <xref:System.Windows.Documents.Table.Columns%2A> kolekce.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vloží novou <xref:System.Windows.Documents.TableColumn>.  Nový sloupec je vložen na pozici indexu 0, což nový první sloupec v tabulce.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableColumnCollection> Kolekce používá standardní indexování od nuly.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá některé libovolné vlastnosti na sloupce ve <xref:System.Windows.Documents.TableColumnCollection> kolekce, která odkazuje na konkrétní sloupce podle indexu.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a>Příklad  
 Následující příklad získá počet sloupců, které jsou aktuálně hostované v tabulce.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere konkrétní sloupec odkazem.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere konkrétní sloupec podle indexu.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere všechny sloupce z kolekce sloupců v tabulce.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled tabulky](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [Definice tabulky pomocí XAML](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [Sestavení tabulky z programu](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)  
 [Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
