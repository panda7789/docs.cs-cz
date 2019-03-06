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
ms.openlocfilehash: e202fe839de547145c36a5664b62c350f40bfce6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379008"
---
# <a name="table-overview"></a>Přehled tabulky
<xref:System.Windows.Documents.Table> je element úrovni bloku, který podporuje předložení mřížky plovoucího obsahu dokumentu. Flexibilita tohoto elementu je velmi užitečné, ale také umožňuje složitější pochopitelný a správně.  
  
 Toto téma obsahuje následující části.  
  
-   [Základní informace o tabulce](#table_basics)  
  
-   [Jaké jsou různé tabulky pak mřížky?](#table_vs_Grid)  
  
-   [Struktura základní tabulky](#basic_table_structure)  
  
-   [Tabulka členství ve skupině](#table_containment)  
  
-   [Seskupení řádků](#row_groupings)  
  
-   [Priorita vykreslení na pozadí](#rendering_precedence)  
  
-   [Pokrývání uzlů řádky nebo sloupce](#spanning_rows_or_columns)  
  
-   [Vytváření tabulky s kódem](#building_a_table_with_code)  
  
-   [Související témata] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>Základní informace o tabulce  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>Jaké jsou různé tabulky pak mřížky?  
 <xref:System.Windows.Documents.Table> a <xref:System.Windows.Controls.Grid> sdílet některé běžné funkce, ale každá je nejvhodnější pro různé scénáře. A <xref:System.Windows.Documents.Table> je určen pro použití v rámci plovoucího obsahu (naleznete v tématu [přehled toku dokumentů](flow-document-overview.md) Další informace o toku obsahu). Mřížka je nejvhodnější používat uvnitř formuláře (v podstatě kdekoli mimo tok obsahu). V rámci <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> podporuje tok obsahu chování jako stránkování přeformátování sloupců a výběru obsahu při <xref:System.Windows.Controls.Grid> nepodporuje. A <xref:System.Windows.Controls.Grid> na druhé straně je vhodné použít mimo <xref:System.Windows.Documents.FlowDocument> z mnoha důvodů včetně <xref:System.Windows.Controls.Grid> přidá prvky podle řádků a sloupců indexu, <xref:System.Windows.Documents.Table> nepodporuje. <xref:System.Windows.Controls.Grid> Element umožňuje vrstvení podřízený obsah, což více než jeden element existovat v jednom "buňky." <xref:System.Windows.Documents.Table> nepodporuje vrstvení. Podřízené prvky <xref:System.Windows.Controls.Grid> může být relativní k oblasti jejich "ohraničením" absolutně umístěné. <xref:System.Windows.Documents.Table> Tato funkce není podporována. A konečně <xref:System.Windows.Controls.Grid> vyžaduje méně prostředků o <xref:System.Windows.Documents.Table> proto zvažte použití <xref:System.Windows.Controls.Grid> ke zlepšení výkonu.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Struktura základní tabulky  
 <xref:System.Windows.Documents.Table> poskytuje prezentace na základě mřížky skládající se z sloupců (reprezentované <xref:System.Windows.Documents.TableColumn> prvky) a řádky (reprezentované <xref:System.Windows.Documents.TableRow> elementy). <xref:System.Windows.Documents.TableColumn> prvky není hostitelem obsahu; jednoduše definovat charakteristiky sloupce a sloupce. <xref:System.Windows.Documents.TableRow> elementy musí být hostovaný ve <xref:System.Windows.Documents.TableRowGroup> element, který definuje seskupení řádků v tabulce. <xref:System.Windows.Documents.TableCell> prvky, které obsahují ze skutečného obsahu, které se budou zobrazovat v tabulce, musí být hostovaný ve <xref:System.Windows.Documents.TableRow> elementu. <xref:System.Windows.Documents.TableCell> může obsahovat pouze prvky, které jsou odvozeny z <xref:System.Windows.Documents.Block>.  Platný podřízené prvky pro <xref:System.Windows.Documents.TableCell> zahrnout.  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell> elementy nemusí přímo hostovat obsah textu. Další informace o pravidlech členství ve skupině pro tok, jako jsou elementy obsahu <xref:System.Windows.Documents.TableCell>, naleznete v tématu [přehled toku dokumentů](flow-document-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table> se podobá <xref:System.Windows.Controls.Grid> prvek ale k dispozici další možnosti a, proto se vyžaduje vyšší režijní náklady na prostředek.  
  
 Následující příklad definuje jednoduchou tabulku s 2 x 3 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Vykreslit základní tabulka](./media/basictablerrender.png "BasicTablerRender")  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Tabulka členství ve skupině  
 <xref:System.Windows.Documents.Table> je odvozen od <xref:System.Windows.Documents.Block> elementu a dodržuje běžných pravidel pro <xref:System.Windows.Documents.Block> úrovně elementy.  A <xref:System.Windows.Documents.Table> prvku mohou být obsaženy pomocí některé z následujících elementů:  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Seskupení řádků  
 <xref:System.Windows.Documents.TableRowGroup> Element poskytuje způsob, jak libovolně seskupení řádků v tabulce, každý řádek v tabulce musí patřit do seskupení řádků.  Řádky v rámci skupiny řádků často sdílejí společné záměr a může být nastaven jako skupinu.  Běžným účelem pro seskupení řádků je k oddělení řádků zvláštní účely, jako je například název, záhlaví a zápatí řádků, od primární obsah obsažen v tabulce.  
  
 Následující příklad používá [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] definovat tabulku s řádky upravený záhlaví a zápatí.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Skupiny řádků tabulky](./media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>Priorita vykreslení na pozadí  
 Vykreslení elementů tabulky v následujícím pořadí (z seřazené od nejnižší po nejvyšší). Toto pořadí nelze změnit. Není třeba žádná vlastnost "Pořadí Z-order" pro tyto elementy, které můžete použít k přepsání této stanovené pořadí.  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 Zvažte následující příklad, který definuje barvy pozadí pro každý z těchto elementů v tabulce.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 Následující obrázek ukazuje, jak v tomto příkladu vykreslí (pouze barvy pozadí zobrazení).  
  
 ![Snímek obrazovky: Tabulky z&#45;pořadí](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Pokrývání uzlů řádky nebo sloupce  
 Buňky tabulky může nakonfigurovat tak, aby span pomocí několika řádků nebo sloupců <xref:System.Windows.Documents.TableCell.RowSpan%2A> nebo <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> atributů.  
  
 Podívejte se na následující příklad, ve kterém buňky zahrnuje tři sloupce.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Pokrývání uzlů všechny tři sloupce buňky](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Vytváření tabulky s kódem  
 Následující příklady ukazují, jak prostřednictvím kódu programu vytvořit <xref:System.Windows.Documents.Table> a jeho naplnění obsah. Obsah tabulky jsou rozdělených do pěti řádcích (reprezentované <xref:System.Windows.Documents.TableRow> objekty obsažené v <xref:System.Windows.Documents.Table.RowGroups%2A> objekt) a šest sloupců (reprezentované <xref:System.Windows.Documents.TableColumn> objekty). Řádky se používají pro účely jiné prezentace, včetně titulní řádek určený pro titulek celou tabulku popisující sloupce dat v tabulce Řádek záhlaví a řádek zápatí se souhrnnými informacemi.  Všimněte si, že pojem "title", "záhlaví" a "zápatí" řádek nepatří do tabulky; Jedná se o jednoduše řádky s různými charakteristikami. Buňky tabulky obsahují skutečný obsah, který se může skládat z textu, obrázků nebo téměř jakýkoli jiný [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.  
  
 První, <xref:System.Windows.Documents.FlowDocument> se vytvoří na hostitele <xref:System.Windows.Documents.Table>a nové <xref:System.Windows.Documents.Table> je vytvořen a přidán do obsahu <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Dále šest <xref:System.Windows.Documents.TableColumn> objekty jsou vytvořen a přidán do tabulky <xref:System.Windows.Documents.Table.Columns%2A> kolekce s některé aplikované formátování.  
  
> [!NOTE]
>  Všimněte si, že v tabulce <xref:System.Windows.Documents.Table.Columns%2A> kolekce používá standardní indexování od nuly.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Titulní řádek v dalším kroku je vytvořen a přidán do tabulky s některé aplikované formátování.  Titulní řádek se stane, tak, aby obsahovala jedinou buňku, která překlenuje všechny šest sloupců v tabulce.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 V dalším kroku řádek záhlaví je vytvořen a přidán do tabulky a buňky v řádku záhlaví jsou vytvořeny a naplněny s obsahem.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 V dalším kroku řádků dat je vytvořen a přidán do tabulky a buňky v tomto řádku jsou vytvořeny a naplněny s obsahem.  Vytváření tento řádek je podobný sestavování řádek záhlaví s mírně odlišné formátování.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Nakonec řádek zápatí vytvořili, přidat a ve formátu.  V zápatí je uvedené jako titulní řádek obsahuje jedinou buňku, která překlenuje všechny šest sloupců v tabulce.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled toku dokumentů](flow-document-overview.md)
- [Definice tabulky pomocí XAML](how-to-define-a-table-with-xaml.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Použití elementů obsahu toku](how-to-use-flow-content-elements.md)
