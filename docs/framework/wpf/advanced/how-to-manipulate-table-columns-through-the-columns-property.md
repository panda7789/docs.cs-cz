---
title: 'Postupy: Zpracování sloupců tabulky prostřednictvím vlastnosti Columns'
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
ms.openlocfilehash: 18a26c76688ebf668293cb1254404d6d2cf15208
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913595"
---
# <a name="how-to-manipulate-a-tables-columns-through-the-columns-property"></a>Postupy: Zpracování sloupců tabulky prostřednictvím vlastnosti Columns
Tento příklad ukazuje některé z nejběžnějších operací, které lze provádět na sloupcích tabulky prostřednictvím <xref:System.Windows.Documents.Table.Columns%2A> vlastnosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou tabulku a poté pomocí <xref:System.Windows.Documents.TableColumnCollection.Add%2A> metody přidá sloupce do <xref:System.Windows.Documents.Table.Columns%2A> kolekce tabulky.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vloží nový <xref:System.Windows.Documents.TableColumn>.  Nový sloupec je vložen na pozici indexu 0, takže se stane novým prvním sloupcem v tabulce.  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableColumnCollection> Kolekce používá standardní indexování založené na nule.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přistupuje k nějakým libovolným vlastnostem pro sloupce <xref:System.Windows.Documents.TableColumnCollection> v kolekci a odkazuje na konkrétní sloupce podle indexu.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a>Příklad  
 Následující příklad získá počet sloupců, které jsou aktuálně hostovány tabulkou.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere konkrétní sloupec odkazem.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere konkrétní sloupec podle indexu.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere všechny sloupce z kolekce Columns tabulky.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled tabulky](table-overview.md)
- [Definice tabulky pomocí XAML](how-to-define-a-table-with-xaml.md)
- [Sestavení tabulky z programu](how-to-build-a-table-programmatically.md)
- [Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
