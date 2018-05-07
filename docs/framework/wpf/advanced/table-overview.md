---
title: Přehled tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
ms.openlocfilehash: 631a14ae8eb17713186f7db66700026cc476024e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="table-overview"></a>Přehled tabulky
<xref:System.Windows.Documents.Table> je úrovně blokovém elementu, které podporuje předložení mřížky obsah dokumentu toku. Flexibilita tohoto elementu je velmi užitečná, ale také umožňuje složitěji, pochopit a používat správně.  
  
 Toto téma obsahuje následující části.  
  
-   [Základní informace o tabulce](#table_basics)  
  
-   [Jak je tabulka různých pak mřížky?](#table_vs_Grid)  
  
-   [Struktura základní tabulky](#basic_table_structure)  
  
-   [Tabulka členství ve skupině](#table_containment)  
  
-   [Seskupení řádků](#row_groupings)  
  
-   [Priorita vykreslování pozadí](#rendering_precedence)  
  
-   [Řádky nebo sloupce](#spanning_rows_or_columns)  
  
-   [Vytvoří tabulku s kódem](#building_a_table_with_code)  
  
-   [Příbuzná témata] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>Základní informace o tabulce  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>Jak je tabulka různých pak mřížky?  
 <xref:System.Windows.Documents.Table> a <xref:System.Windows.Controls.Grid> sdílet některé běžné funkce, ale každý je nejvhodnější pro různé scénáře. A <xref:System.Windows.Documents.Table> je určená pro použití v rámci toku obsahu (najdete v části [toku dokumentu přehled](../../../../docs/framework/wpf/advanced/flow-document-overview.md) Další informace o toku obsahu). Mřížky jsou nejvhodnější uvnitř forms (v podstatě kamkoli mimo toku obsahu). V rámci <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> podporuje toku obsahu chování jako stránkování, přeformátování sloupců a výběru obsahu při <xref:System.Windows.Controls.Grid> neexistuje. A <xref:System.Windows.Controls.Grid> na druhé straně je nejvhodnější mimo <xref:System.Windows.Documents.FlowDocument> z mnoha důvodů včetně <xref:System.Windows.Controls.Grid> přidá elementy podle řádků a sloupců index, <xref:System.Windows.Documents.Table> neexistuje. <xref:System.Windows.Controls.Grid> Element umožňuje rozvrstvení podřízené obsahu, povolení více než jeden element existovat v jednom "buňky." <xref:System.Windows.Documents.Table> nepodporuje rozvrstvení. Podřízených elementů <xref:System.Windows.Controls.Grid> možné absolutně umístit relativně k oblasti hranic jejich "buňky". <xref:System.Windows.Documents.Table> Tato funkce není podporována. Nakonec <xref:System.Windows.Controls.Grid> vyžaduje méně prostředků pak <xref:System.Windows.Documents.Table> , zvažte použití <xref:System.Windows.Controls.Grid> ke zlepšení výkonu.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Struktura základní tabulky  
 <xref:System.Windows.Documents.Table> poskytuje na základě mřížky prezentace skládající se z sloupců (reprezentována <xref:System.Windows.Documents.TableColumn> prvky) a řádky (reprezentována <xref:System.Windows.Documents.TableRow> elementy). <xref:System.Windows.Documents.TableColumn> elementy nejsou hostiteli obsahu; jednoduše definovat sloupce a vlastnosti sloupců. <xref:System.Windows.Documents.TableRow> elementy musí být uloženy ve <xref:System.Windows.Documents.TableRowGroup> element, který definuje seskupení řádků v tabulce. <xref:System.Windows.Documents.TableCell> elementy, které obsahují skutečný obsah předávané tabulky, musí být uloženy ve <xref:System.Windows.Documents.TableRow> elementu. <xref:System.Windows.Documents.TableCell> může obsahovat jenom elementy, které jsou odvozeny od <xref:System.Windows.Documents.Block>.  Platný podřízené elementy pro <xref:System.Windows.Documents.TableCell> zahrnout.  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell> elementy nemusí hostovat přímo textového obsahu. Další informace o členství ve skupině pravidla pro tok obsahu elementy jako <xref:System.Windows.Documents.TableCell>, najdete v části [toku dokumentu přehled](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table> je podobná <xref:System.Windows.Controls.Grid> element ale k dispozici další možnosti a, proto vyžaduje větší režijní náklady na prostředek.  
  
 V následujícím příkladu definuje jednoduché tabulce 2 × 3 s [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Vykreslení základní tabulky](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Tabulka členství ve skupině  
 <xref:System.Windows.Documents.Table> odvozená z <xref:System.Windows.Documents.Block> elementu a dodržuje běžné pravidla pro <xref:System.Windows.Documents.Block> elementů na úrovni.  A <xref:System.Windows.Documents.Table> element mohou být obsaženy kterýmkoli z těchto prvků:  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Seskupení řádků  
 <xref:System.Windows.Documents.TableRowGroup> Element poskytuje způsob, jak nahodile seskupení řádků v tabulce; každý řádek v tabulce musí patřit do seskupení řádků.  Řádky v rámci skupiny řádek často sdílet běžné záměr a může být ve tvaru skupinu.  Běžně používá pro seskupení řádků je oddělení speciální řádky, například název, záhlaví a zápatí řádky, z primární obsahu obsažených v tabulce.  
  
 Následující příklad používá [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] definovat tabulku s řádky stylem záhlaví a zápatí stránky.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Tabulky skupin řádků](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>Priorita vykreslování pozadí  
 V následujícím pořadí (pořadí z-order od nejnižší na nejvyšší) vykreslení elementů tabulky. Toto pořadí nelze změnit. Například neexistuje vlastnost "Pořadí vykreslování" pro tyto elementy, které můžete použít k přepsání tohoto pořadí zavedených.  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 Vezměte v úvahu následující příklad, který definuje barvy pozadí pro každou z těchto elementů v tabulce.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 Následující obrázek ukazuje, jak tento příklad vykreslí (pouze barvy pozadí zobrazující).  
  
 ![Snímek obrazovky: Tabulky z&#45;pořadí](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Řádky nebo sloupce  
 Buněk tabulky může být nakonfigurována rozložit více řádků nebo sloupce s použitím <xref:System.Windows.Documents.TableCell.RowSpan%2A> nebo <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> atributy v uvedeném pořadí.  
  
 Podívejte se na následující příklad, ve kterém buňku zahrnuje tři sloupce.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Buňka pokrývání uzlů všechny tři sloupce](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Vytvoří tabulku s kódem  
 Následující příklady ukazují, jak vytvořit prostřednictvím kódu programu <xref:System.Windows.Documents.Table> a jeho naplnění obsah. Obsah v tabulce jsou rozdělených do pěti řádků (reprezentována <xref:System.Windows.Documents.TableRow> objekty obsažené v <xref:System.Windows.Documents.Table.RowGroups%2A> objekt) a šesti sloupců (reprezentována <xref:System.Windows.Documents.TableColumn> objektů). Řádky se používají pro účely různých prezentace, včetně názvu řádek má title celou tabulku popisující sloupce dat v tabulce Řádek záhlaví a zápatí řádek s souhrnné informace.  Všimněte si, že znalost problematicky "title", "záhlaví" a "zápatí" řádků nepatří do tabulky; Jedná se o jednoduše řádky s různými charakteristikami. Buněk tabulky obsahují skutečný obsah, který se může skládat z text, obrázky nebo téměř žádné jiné [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.  
  
 První, <xref:System.Windows.Documents.FlowDocument> je vytvořena na hostitele <xref:System.Windows.Documents.Table>a nový <xref:System.Windows.Documents.Table> je vytvořen a přidán k obsahu <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Další, půl <xref:System.Windows.Documents.TableColumn> objekty jsou vytvořeny a do tabulky přidat <xref:System.Windows.Documents.Table.Columns%2A> kolekce s některé formátování použít.  
  
> [!NOTE]
>  Všimněte si, že v tabulce <xref:System.Windows.Documents.Table.Columns%2A> kolekce používá standardní indexování od nuly.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Řádek název v dalším kroku je vytvořen a přidán do tabulky s některé formátování použité.  Název řádek se stane obsahovat jednu buňku, která zahrnuje všechny šesti sloupce v tabulce.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 V dalším kroku se vytvoří a přidat do tabulky řádek záhlaví a buňky v řádku záhlaví jsou vytvořeny a naplněny s obsahem.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 V dalším kroku se vytvoří a přidat do tabulky řádek pro data, a v buňkách v tomto řádku jsou vytvořeny a naplněny s obsahem.  Vytváření tento řádek je podobná vytváření řádek záhlaví s použitým formátováním mírně lišit.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Nakonec řádek zápatí vytvářet, přidat a formátovat.  Jako název řádek zápatí obsahuje jednu buňku, která zahrnuje všechny šesti sloupce v tabulce.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled toku dokumentů](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [Definice tabulky pomocí XAML](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Použití elementů obsahu toku](../../../../docs/framework/wpf/advanced/how-to-use-flow-content-elements.md)
