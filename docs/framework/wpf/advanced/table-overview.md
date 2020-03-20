---
title: Přehled tabulek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
ms.openlocfilehash: 4bd747cea43755116c56b16f1de9a6ffb59935ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187274"
---
# <a name="table-overview"></a>Přehled tabulek
<xref:System.Windows.Documents.Table>je prvek na úrovni bloku, který podporuje prezentaci obsahu dokumentu Flow na základě mřížky. Flexibilita tohoto prvku je velmi užitečná, ale také ztěžuje pochopení a správné používání.  
  
 Toto téma obsahuje tyto části:  
  
- [Základy tabulky](#table_basics)  
  
- [Jak se tabulka liší pak Grid?](#table_vs_Grid)  
  
- [Základní struktura tabulky](#basic_table_structure)  
  
- [Uzavření tabulky](#table_containment)  
  
- [Seskupení řádků](#row_groupings)  
  
- [Priorita vykreslování na pozadí](#rendering_precedence)  
  
- [Překrývání řádků nebo sloupců](#spanning_rows_or_columns)  
  
- [Vytváření tabulky s kódem](#building_a_table_with_code)  
  
- [Příbuzná témata]
  
<a name="table_basics"></a>
## <a name="table-basics"></a>Základy tabulky  
  
<a name="table_vs_Grid"></a>
### <a name="how-is-table-different-then-grid"></a>Jak se tabulka liší pak Grid?  
 <xref:System.Windows.Documents.Table>a <xref:System.Windows.Controls.Grid> sdílet některé běžné funkce, ale každý je nejvhodnější pro různé scénáře. A <xref:System.Windows.Documents.Table> je určen pro použití v rámci obsahu toku (viz [Přehled toku dokumentu](flow-document-overview.md) pro další informace o obsahu toku). Mřížky se nejlépe používají uvnitř formulářů (v podstatě kdekoli mimo obsah toku). V <xref:System.Windows.Documents.FlowDocument>rámci <xref:System.Windows.Documents.Table> , podporuje chování obsahu toku, jako je stránkování, přeformátování sloupců a výběr obsahu, zatímco <xref:System.Windows.Controls.Grid> a není. A <xref:System.Windows.Controls.Grid> na druhé straně se nejlépe <xref:System.Windows.Documents.FlowDocument> používá mimo <xref:System.Windows.Controls.Grid> z mnoha důvodů, včetně <xref:System.Windows.Documents.Table> přidá prvky založené na řádku a sloupec index, není. Prvek <xref:System.Windows.Controls.Grid> umožňuje vrstvení podřízeného obsahu, což umožňuje více než jeden prvek existovat v rámci jedné "buňky". <xref:System.Windows.Documents.Table>nepodporuje vrstvení. Podřízené <xref:System.Windows.Controls.Grid> prvky může být absolutně umístěn vzhledem k oblasti jejich "buňky" hranice. <xref:System.Windows.Documents.Table>nepodporuje tuto funkci. Nakonec vyžaduje <xref:System.Windows.Controls.Grid> méně prostředků <xref:System.Windows.Documents.Table> pak tak <xref:System.Windows.Controls.Grid> zvážit použití ke zlepšení výkonu.  
  
<a name="basic_table_structure"></a>
### <a name="basic-table-structure"></a>Základní struktura tabulky  
 <xref:System.Windows.Documents.Table>poskytuje prezentaci založenou na mřížce skládající se ze sloupců (reprezentované <xref:System.Windows.Documents.TableColumn> prvky) a řádků (reprezentované <xref:System.Windows.Documents.TableRow> prvky). <xref:System.Windows.Documents.TableColumn>prvky nehostují obsah; jednoduše definují sloupce a charakteristiky sloupců. <xref:System.Windows.Documents.TableRow>prvky musí být <xref:System.Windows.Documents.TableRowGroup> hostovány v elementu, který definuje seskupení řádků pro tabulku. <xref:System.Windows.Documents.TableCell>prvky, které obsahují skutečný obsah, který má být předložen <xref:System.Windows.Documents.TableRow> v tabulce, musí být hostovány v prvku. <xref:System.Windows.Documents.TableCell>mohou obsahovat pouze <xref:System.Windows.Documents.Block>prvky, které jsou odvozeny z .  Platné podřízené <xref:System.Windows.Documents.TableCell> prvky pro include.  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableCell>prvky nemusí přímo hostovat textový obsah. Další informace o pravidlech uzavření pro <xref:System.Windows.Documents.TableCell>prvky obsahu toku, jako je , naleznete [v tématu Přehled dokumentu toku](flow-document-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table>je podobný <xref:System.Windows.Controls.Grid> prvku, ale má více možností a proto vyžaduje větší režii prostředků.  
  
 Následující příklad definuje jednoduchou tabulku 2 x 3 s XAML.  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 Následující obrázek ukazuje, jak se tento příklad vykresluje.  
  
 ![Snímek obrazovky, který ukazuje, jak se vykresluje základní tabulka.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>
### <a name="table-containment"></a>Uzavření tabulky  
 <xref:System.Windows.Documents.Table>odvozuje <xref:System.Windows.Documents.Block> z prvku a dodržuje společná <xref:System.Windows.Documents.Block> pravidla pro prvky úrovně.  Prvek <xref:System.Windows.Documents.Table> může být obsažen v některém z těchto prvků:  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>
### <a name="row-groupings"></a>Seskupení řádků  
 Prvek <xref:System.Windows.Documents.TableRowGroup> poskytuje způsob, jak libovolně seskupit řádky v rámci tabulky; každý řádek v tabulce musí patřit do seskupení řádků.  Řádky ve skupině řádků často sdílejí společný záměr a mohou být stylizovány jako skupina.  Pro seskupení řádků se běžně používá oddělení řádků pro speciální účely, například řádků nadpisů, záhlaví a zápatí, od primárního obsahu obsaženého v tabulce.  
  
 Následující příklad používá XAML k definování tabulky se stylizovanými řádky záhlaví a zápatí.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 Následující obrázek ukazuje, jak se tento příklad vykresluje.  
  
 ![Snímek obrazovky: Skupiny řádků tabulky](./media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>
### <a name="background-rendering-precedence"></a>Priorita vykreslování na pozadí  
 Prvky tabulky se vykreslují v následujícím pořadí (pořadí vykreslování od nejnižší po nejvyšší). Toto pořadí nelze změnit. Například neexistuje žádná vlastnost "Pořadí vykreslovat" pro tyto prvky, které můžete použít k přepsání tohoto zavedeného pořadí.  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 Vezměme si následující příklad, který definuje barvy pozadí pro každý z těchto prvků v tabulce.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 Následující obrázek ukazuje, jak se tento příklad vykresluje (zobrazuje pouze barvy pozadí).  
  
 ![Snímek obrazovky: Tabulka z&#45;pořadí](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>
### <a name="spanning-rows-or-columns"></a>Překrývání řádků nebo sloupců  
 Buňky tabulky mohou být nakonfigurovány tak, <xref:System.Windows.Documents.TableCell.RowSpan%2A> <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> aby se rozprostíraly na více řádků nebo sloupců pomocí atributů nebo.  
  
 Vezměme si následující příklad, ve kterém buňka pokrývá tři sloupce.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 Následující obrázek ukazuje, jak se tento příklad vykresluje.  
  
 ![Snímek obrazovky: Buňka zahrnující všechny tři sloupce](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>
## <a name="building-a-table-with-code"></a>Vytváření tabulky s kódem  
 Následující příklady ukazují, jak programově <xref:System.Windows.Documents.Table> vytvořit a naplnit obsahem. Obsah tabulky je rozdělen do pěti řádků (reprezentovaných objekty obsaženými <xref:System.Windows.Documents.TableRow> v objektu) <xref:System.Windows.Documents.Table.RowGroups%2A> a šesti sloupcích (reprezentovaných objekty). <xref:System.Windows.Documents.TableColumn> Řádky se používají pro různé účely prezentace, včetně řádku nadpisu určeného k označení celé tabulky, řádku záhlaví popisujícího sloupce dat v tabulce a řádku zápatí se souhrnnými informacemi.  Všimněte si, že pojem "název", "záhlaví" a "zápatí" řádky nejsou vlastní tabulce; jedná se jednoduše o řádky s různými vlastnostmi. Buňky tabulky obsahují skutečný obsah, který může být tvořen textem, obrázky nebo téměř jakýmkoli jiným [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] prvkem.  
  
 Nejprve <xref:System.Windows.Documents.FlowDocument> a je vytvořen <xref:System.Windows.Documents.Table>pro hostování <xref:System.Windows.Documents.Table> , a nový je <xref:System.Windows.Documents.FlowDocument>vytvořen a přidán do obsahu .  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Dále šest <xref:System.Windows.Documents.TableColumn> objektů jsou vytvořeny a přidány <xref:System.Windows.Documents.Table.Columns%2A> do kolekce tabulky, s některé formátování použít.  
  
> [!NOTE]
> Všimněte si, <xref:System.Windows.Documents.Table.Columns%2A> že kolekce tabulky používá standardní indexování s nulou.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Dále je vytvořen řádek nadpisu a přidán do tabulky s použitým formátováním.  Řádek nadpisu obsahuje jednu buňku, která pokrývá všech šest sloupců v tabulce.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Dále je vytvořen řádek záhlaví a přidán do tabulky a buňky v řádku záhlaví jsou vytvořeny a naplněny obsahem.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Dále je vytvořen řádek pro data a přidán do tabulky a buňky v tomto řádku jsou vytvořeny a naplněny obsahem.  Vytvoření tohoto řádku je podobné vytváření řádku záhlaví s mírně odlišným formátováním.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Nakonec je vytvořen, přidán a formátován řádek zápatí.  Podobně jako titulní řádek obsahuje zápatí jednu buňku, která pokrývá všech šest sloupců v tabulce.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Viz také

- [Přehled toku dokumentů](flow-document-overview.md)
- [Definování tabulky pomocí jazyka XAML](how-to-define-a-table-with-xaml.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Použití elementů obsahu toku](how-to-use-flow-content-elements.md)
