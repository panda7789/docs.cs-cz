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
ms.openlocfilehash: fa7106207c69f19b647ba80ab7e724e9aad174c1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005074"
---
# <a name="table-overview"></a>Přehled tabulky
<xref:System.Windows.Documents.Table> je prvek na úrovni bloku, který podporuje prezentaci na základě mřížky obsahu dokumentu toku. Flexibilita tohoto prvku je velmi užitečná, ale také usnadňuje pochopení a používání správně.  
  
 Toto téma obsahuje následující části.  
  
- [Základy tabulek](#table_basics)  
  
- [Jak je tabulka odlišná pro mřížku?](#table_vs_Grid)  
  
- [Základní struktura tabulky](#basic_table_structure)  
  
- [Zahrnutí tabulky](#table_containment)  
  
- [Seskupení řádků](#row_groupings)  
  
- [Priorita vykreslování na pozadí](#rendering_precedence)  
  
- [Pokrývání řádků nebo sloupců](#spanning_rows_or_columns)  
  
- [Vytvoření tabulky s kódem](#building_a_table_with_code)  
  
- [Související témata] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>Základy tabulek  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>Jak je tabulka odlišná pro mřížku?  
 <xref:System.Windows.Documents.Table> a <xref:System.Windows.Controls.Grid> sdílet některé běžné funkce, ale každá z nich nejlépe vyhovuje různým scénářům. <xref:System.Windows.Documents.Table> je navržený pro použití v rámci obsahu toku (Další informace o obsahu toku najdete v tématu [Přehled dokumentů flowu](flow-document-overview.md) ). Mřížky se nejlépe používají ve formulářích (v podstatě kdekoli mimo obsah toku). V rámci <xref:System.Windows.Documents.FlowDocument><xref:System.Windows.Documents.Table> podporuje chování toku obsahu, jako jsou stránkování, přetékání sloupců a výběr obsahu, zatímco <xref:System.Windows.Controls.Grid> ne. <xref:System.Windows.Controls.Grid> na druhé straně se nejlépe využije mimo <xref:System.Windows.Documents.FlowDocument> z mnoha důvodů, včetně <xref:System.Windows.Controls.Grid> přidá prvky založené na indexu řádků a sloupců, <xref:System.Windows.Documents.Table> ne. Element <xref:System.Windows.Controls.Grid> umožňuje vrstvení podřízeného obsahu, což umožňuje, aby v jedné "buňce" existoval více než jeden prvek. <xref:System.Windows.Documents.Table> nepodporuje vrstvení. Podřízené prvky <xref:System.Windows.Controls.Grid> mohou být absolutně umístěny relativně k oblasti jejich hranic "buňka". <xref:System.Windows.Documents.Table> tuto funkci nepodporuje. Nakonec <xref:System.Windows.Controls.Grid> vyžaduje méně prostředků, a proto byste měli <xref:System.Windows.Documents.Table> zvážit použití <xref:System.Windows.Controls.Grid> ke zvýšení výkonu.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Základní struktura tabulky  
 <xref:System.Windows.Documents.Table> poskytuje prezentaci založenou na mřížce sestávající ze sloupců (reprezentovaných <xref:System.Windows.Documents.TableColumn> prvky) a řádků (reprezentovaných prvky <xref:System.Windows.Documents.TableRow>). prvky <xref:System.Windows.Documents.TableColumn> neobsahují hostování obsahu; jednoduše definují sloupce a charakteristiky sloupců. prvky <xref:System.Windows.Documents.TableRow> musí být hostovány v <xref:System.Windows.Documents.TableRowGroup> elementu, který definuje seskupení řádků pro tabulku. prvky <xref:System.Windows.Documents.TableCell>, které obsahují skutečný obsah, který má být prezentován tabulkou, musí být hostovány v <xref:System.Windows.Documents.TableRow> elementu. <xref:System.Windows.Documents.TableCell> může obsahovat pouze prvky, které jsou odvozeny z <xref:System.Windows.Documents.Block>.  Platné podřízené prvky pro <xref:System.Windows.Documents.TableCell> zahrnují.  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> prvky <xref:System.Windows.Documents.TableCell> nemůžou přímo hostovat textový obsah. Další informace o pravidlech omezení pro prvky obsahu toku, jako je <xref:System.Windows.Documents.TableCell>, naleznete v tématu [Flow Flow Overview](flow-document-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table> je podobná <xref:System.Windows.Controls.Grid>mu prvku, ale má více možností, a proto vyžaduje větší nároky na prostředky.  
  
 V následujícím příkladu je definována Jednoduchá tabulka 2 x 3 s XAML.  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 Následující obrázek ukazuje, jak tento příklad vykresluje.  
  
 ![Snímek obrazovky, který ukazuje, jak vykreslí základní tabulka](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Zahrnutí tabulky  
 <xref:System.Windows.Documents.Table> je odvozen z prvku <xref:System.Windows.Documents.Block> a dodržuje společná pravidla pro <xref:System.Windows.Documents.Block> prvků na úrovni.  Element <xref:System.Windows.Documents.Table> může být obsažený v některém z následujících elementů:  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Seskupení řádků  
 Element <xref:System.Windows.Documents.TableRowGroup> poskytuje způsob, jak v tabulce libovolně seskupovat řádky; Každý řádek v tabulce musí patřit do seskupení řádků.  Řádky v rámci skupiny řádků často sdílejí běžný záměr a můžou být ve stylu jako skupina.  Běžné použití pro seskupení řádků je samostatné řádky, jako je název, hlavička a řádky zápatí, od primárního obsahu obsaženého v tabulce.  
  
 Následující příklad používá XAML k definování tabulky se stylem řádky záhlaví a zápatí.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 Následující obrázek ukazuje, jak tento příklad vykresluje.  
  
 ![Snímek obrazovky: Table_RowGroups skupiny řádků tabulky](./media/table-rowgroups.png "")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>Priorita vykreslování na pozadí  
 Prvky tabulky se vykreslují v následujícím pořadí (pořadí z od nejnižší po nejvyšší). Tuto objednávku nelze změnit. Například neexistuje žádná vlastnost "Z-order" pro tyto prvky, které lze použít k přepsání tohoto navázaného pořadí.  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 Vezměte v úvahu následující příklad, který definuje barvy pozadí pro každý z těchto prvků v tabulce.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 Následující obrázek ukazuje, jak tento příklad vykresluje (zobrazí pouze barvy pozadí).  
  
 ![Snímek obrazovky:&#45;Table_ZOrder pořadí z tabulky](./media/table-zorder.png "")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Pokrývání řádků nebo sloupců  
 Buňky tabulky můžou být nakonfigurované tak, aby pokrývají více řádků nebo sloupců pomocí atributů <xref:System.Windows.Documents.TableCell.RowSpan%2A> nebo <xref:System.Windows.Documents.TableCell.ColumnSpan%2A>, v uvedeném pořadí.  
  
 Vezměte v úvahu následující příklad, ve kterém buňka zahrnuje tři sloupce.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 Následující obrázek ukazuje, jak tento příklad vykresluje.  
  
 ![Snímek obrazovky: buňky zahrnující všechny tři sloupce](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Vytvoření tabulky s kódem  
 Následující příklady ukazují, jak programově vytvořit <xref:System.Windows.Documents.Table> a naplnit ho obsahem. Obsah tabulky se rozdělí na pět řádků (reprezentovaných <xref:System.Windows.Documents.TableRow> objekty obsaženými v objektu <xref:System.Windows.Documents.Table.RowGroups%2A>) a šesti sloupcích (reprezentované objekty <xref:System.Windows.Documents.TableColumn>). Řádky se používají pro různé účely prezentace, včetně řádku názvu, který je určený k nadpisu celé tabulky, řádku záhlaví, který popisuje sloupce dat v tabulce a řádek zápatí se souhrnnými informacemi.  Všimněte si, že pojem "title", "header" a "Foot" řádky nejsou podstatou tabulky; Jedná se o jednoduché řádky s různými charakteristikami. Buňky tabulky obsahují skutečný obsah, který se může skládat z textu, obrázků nebo téměř jakéhokoli jiného prvku [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 Nejprve se vytvoří <xref:System.Windows.Documents.FlowDocument> pro hostování <xref:System.Windows.Documents.Table>a vytvoří se nový <xref:System.Windows.Documents.Table>, který se přidá k obsahu <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 V dalším kroku se vytvoří šest <xref:System.Windows.Documents.TableColumn> objektů a přidají se do kolekce <xref:System.Windows.Documents.Table.Columns%2A> tabulky s použitím některých formátování.  
  
> [!NOTE]
> Všimněte si, že kolekce <xref:System.Windows.Documents.Table.Columns%2A> tabulky používá standardní indexování založené na nule.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 V dalším kroku se vytvoří řádek s nadpisem a přidá se do tabulky s některým použitým formátováním.  Řádek nadpisu obsahuje jednu buňku, která zahrnuje všechny šest sloupců v tabulce.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 V dalším kroku se vytvoří řádek záhlaví a přidá se do tabulky a buňky v řádku záhlaví se vytvoří a naplní se obsahem.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 V dalším kroku se vytvoří řádek pro data a přidají se do tabulky a buňky v tomto řádku se vytvoří a naplní se obsahem.  Sestavování tohoto řádku se podobá vytvoření řádku záhlaví s mírně odlišným formátováním.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Nakonec se vytvoří, přidá a naformátuje řádek zápatí.  Podobně jako u řádku nadpisu obsahuje zápatí jedinou buňku, která zahrnuje všechny šest sloupců v tabulce.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled toku dokumentů](flow-document-overview.md)
- [Definice tabulky pomocí XAML](how-to-define-a-table-with-xaml.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Použití elementů obsahu toku](how-to-use-flow-content-elements.md)
