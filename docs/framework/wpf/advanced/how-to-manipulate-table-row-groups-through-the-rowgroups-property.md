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
---
# <a name="how-to-manipulate-a-table39s-row-groups-through-the-rowgroups-property"></a>Postupy: manipulace s tabulku&#39;skupin řádků s prostřednictvím vlastnosti RowGroups
Tento příklad ukazuje některé z nejčastěji operací, které lze provést na skupiny řádků tabulky prostřednictvím <xref:System.Windows.Documents.Table.RowGroups%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou tabulku a potom pomocí <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> metody přidat sloupce do tabulky <xref:System.Windows.Documents.Table.RowGroups%2A> kolekce.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vloží novou <xref:System.Windows.Documents.TableRowGroup>.  Je na pozici indexu 0, což nový první řádek vložit nový sloupec v tabulce.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableRowGroupCollection> Kolekce používá standardní indexování od nuly.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá několik řádků ke konkrétní <xref:System.Windows.Documents.TableRowGroup> (zadán indexem) v tabulce.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá některé libovolné vlastnosti v řádcích ve skupině první řádek v tabulce.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přidá několika buněk ke konkrétní <xref:System.Windows.Documents.TableRow> (zadán indexem) v tabulce.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přístup některé libovolné metody a vlastnosti buněk v první řádek v první skupiny řádků.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí počet <xref:System.Windows.Documents.TableRowGroup> elementy, které jsou hostované v tabulce.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere skupinu konkrétního řádku odkazem.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere skupinu konkrétního řádku index.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere všechny skupiny řádků z kolekce skupin řádků v tabulce.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Manipulace s prvky toku obsahu prostřednictvím vlastnosti Inlines](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Zpracování sloupců tabulky prostřednictvím vlastnosti Columns](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)
