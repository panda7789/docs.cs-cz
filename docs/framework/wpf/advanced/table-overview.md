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
ms.openlocfilehash: 01ab11d8e3c1d2c84514770816ca9c9eab0835b6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649180"
---
# <a name="table-overview"></a><span data-ttu-id="5439c-102">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="5439c-102">Table Overview</span></span>
<span data-ttu-id="5439c-103"><xref:System.Windows.Documents.Table> je element úrovni bloku, který podporuje předložení mřížky plovoucího obsahu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5439c-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="5439c-104">Flexibilita tohoto elementu je velmi užitečné, ale také umožňuje složitější pochopitelný a správně.</span><span class="sxs-lookup"><span data-stu-id="5439c-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="5439c-105">Toto téma obsahuje následující části.</span><span class="sxs-lookup"><span data-stu-id="5439c-105">This topic contains the following sections.</span></span>  
  
- [<span data-ttu-id="5439c-106">Základní informace o tabulce</span><span class="sxs-lookup"><span data-stu-id="5439c-106">Table Basics</span></span>](#table_basics)  
  
- [<span data-ttu-id="5439c-107">Jaké jsou různé tabulky pak mřížky?</span><span class="sxs-lookup"><span data-stu-id="5439c-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
- [<span data-ttu-id="5439c-108">Struktura základní tabulky</span><span class="sxs-lookup"><span data-stu-id="5439c-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
- [<span data-ttu-id="5439c-109">Tabulka členství ve skupině</span><span class="sxs-lookup"><span data-stu-id="5439c-109">Table Containment</span></span>](#table_containment)  
  
- [<span data-ttu-id="5439c-110">Seskupení řádků</span><span class="sxs-lookup"><span data-stu-id="5439c-110">Row Groupings</span></span>](#row_groupings)  
  
- [<span data-ttu-id="5439c-111">Priorita vykreslení na pozadí</span><span class="sxs-lookup"><span data-stu-id="5439c-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
- [<span data-ttu-id="5439c-112">Pokrývání uzlů řádky nebo sloupce</span><span class="sxs-lookup"><span data-stu-id="5439c-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
- [<span data-ttu-id="5439c-113">Vytváření tabulky s kódem</span><span class="sxs-lookup"><span data-stu-id="5439c-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
- <span data-ttu-id="5439c-114">[Související témata]</span><span class="sxs-lookup"><span data-stu-id="5439c-114">[Related Topics]</span></span> 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a><span data-ttu-id="5439c-115">Základní informace o tabulce</span><span class="sxs-lookup"><span data-stu-id="5439c-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="5439c-116">Jaké jsou různé tabulky pak mřížky?</span><span class="sxs-lookup"><span data-stu-id="5439c-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="5439c-117"><xref:System.Windows.Documents.Table> a <xref:System.Windows.Controls.Grid> sdílet některé běžné funkce, ale každá je nejvhodnější pro různé scénáře.</span><span class="sxs-lookup"><span data-stu-id="5439c-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="5439c-118">A <xref:System.Windows.Documents.Table> je určen pro použití v rámci plovoucího obsahu (naleznete v tématu [přehled toku dokumentů](flow-document-overview.md) Další informace o toku obsahu).</span><span class="sxs-lookup"><span data-stu-id="5439c-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="5439c-119">Mřížka je nejvhodnější používat uvnitř formuláře (v podstatě kdekoli mimo tok obsahu).</span><span class="sxs-lookup"><span data-stu-id="5439c-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="5439c-120">V rámci <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> podporuje tok obsahu chování jako stránkování přeformátování sloupců a výběru obsahu při <xref:System.Windows.Controls.Grid> nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="5439c-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="5439c-121">A <xref:System.Windows.Controls.Grid> na druhé straně je vhodné použít mimo <xref:System.Windows.Documents.FlowDocument> z mnoha důvodů včetně <xref:System.Windows.Controls.Grid> přidá prvky podle řádků a sloupců indexu, <xref:System.Windows.Documents.Table> nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="5439c-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="5439c-122"><xref:System.Windows.Controls.Grid> Element umožňuje vrstvení podřízený obsah, což více než jeden element existovat v jednom "buňky."</span><span class="sxs-lookup"><span data-stu-id="5439c-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="5439c-123"><xref:System.Windows.Documents.Table> nepodporuje vrstvení.</span><span class="sxs-lookup"><span data-stu-id="5439c-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="5439c-124">Podřízené prvky <xref:System.Windows.Controls.Grid> může být relativní k oblasti jejich "ohraničením" absolutně umístěné.</span><span class="sxs-lookup"><span data-stu-id="5439c-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="5439c-125"><xref:System.Windows.Documents.Table> Tato funkce není podporována.</span><span class="sxs-lookup"><span data-stu-id="5439c-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="5439c-126">A konečně <xref:System.Windows.Controls.Grid> vyžaduje méně prostředků o <xref:System.Windows.Documents.Table> proto zvažte použití <xref:System.Windows.Controls.Grid> ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="5439c-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a><span data-ttu-id="5439c-127">Struktura základní tabulky</span><span class="sxs-lookup"><span data-stu-id="5439c-127">Basic Table Structure</span></span>  
 <span data-ttu-id="5439c-128"><xref:System.Windows.Documents.Table> poskytuje prezentace na základě mřížky skládající se z sloupců (reprezentované <xref:System.Windows.Documents.TableColumn> prvky) a řádky (reprezentované <xref:System.Windows.Documents.TableRow> elementy).</span><span class="sxs-lookup"><span data-stu-id="5439c-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="5439c-129"><xref:System.Windows.Documents.TableColumn> prvky není hostitelem obsahu; jednoduše definovat charakteristiky sloupce a sloupce.</span><span class="sxs-lookup"><span data-stu-id="5439c-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="5439c-130"><xref:System.Windows.Documents.TableRow> elementy musí být hostovaný ve <xref:System.Windows.Documents.TableRowGroup> element, který definuje seskupení řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="5439c-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="5439c-131"><xref:System.Windows.Documents.TableCell> prvky, které obsahují ze skutečného obsahu, které se budou zobrazovat v tabulce, musí být hostovaný ve <xref:System.Windows.Documents.TableRow> elementu.</span><span class="sxs-lookup"><span data-stu-id="5439c-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="5439c-132"><xref:System.Windows.Documents.TableCell> může obsahovat pouze prvky, které jsou odvozeny z <xref:System.Windows.Documents.Block>.</span><span class="sxs-lookup"><span data-stu-id="5439c-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="5439c-133">Platný podřízené prvky pro <xref:System.Windows.Documents.TableCell> zahrnout.</span><span class="sxs-lookup"><span data-stu-id="5439c-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <span data-ttu-id="5439c-134"><xref:System.Windows.Documents.TableCell> elementy nemusí přímo hostovat obsah textu.</span><span class="sxs-lookup"><span data-stu-id="5439c-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="5439c-135">Další informace o pravidlech členství ve skupině pro tok, jako jsou elementy obsahu <xref:System.Windows.Documents.TableCell>, naleznete v tématu [přehled toku dokumentů](flow-document-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5439c-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](flow-document-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5439c-136"><xref:System.Windows.Documents.Table> se podobá <xref:System.Windows.Controls.Grid> prvek ale k dispozici další možnosti a, proto se vyžaduje vyšší režijní náklady na prostředek.</span><span class="sxs-lookup"><span data-stu-id="5439c-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="5439c-137">Následující příklad definuje jednoduchou tabulku s 2 x 3 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5439c-137">The following example defines a simple 2 x 3 table with [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="5439c-138">Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="5439c-138">The following figure shows how this example renders.</span></span>  
  
 ![Snímek obrazovky zobrazující, jak se vykreslí základní tabulky.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a><span data-ttu-id="5439c-140">Tabulka členství ve skupině</span><span class="sxs-lookup"><span data-stu-id="5439c-140">Table Containment</span></span>  
 <span data-ttu-id="5439c-141"><xref:System.Windows.Documents.Table> je odvozen od <xref:System.Windows.Documents.Block> elementu a dodržuje běžných pravidel pro <xref:System.Windows.Documents.Block> úrovně elementy.</span><span class="sxs-lookup"><span data-stu-id="5439c-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="5439c-142">A <xref:System.Windows.Documents.Table> prvku mohou být obsaženy pomocí některé z následujících elementů:</span><span class="sxs-lookup"><span data-stu-id="5439c-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a><span data-ttu-id="5439c-143">Seskupení řádků</span><span class="sxs-lookup"><span data-stu-id="5439c-143">Row Groupings</span></span>  
 <span data-ttu-id="5439c-144"><xref:System.Windows.Documents.TableRowGroup> Element poskytuje způsob, jak libovolně seskupení řádků v tabulce, každý řádek v tabulce musí patřit do seskupení řádků.</span><span class="sxs-lookup"><span data-stu-id="5439c-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="5439c-145">Řádky v rámci skupiny řádků často sdílejí společné záměr a může být nastaven jako skupinu.</span><span class="sxs-lookup"><span data-stu-id="5439c-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="5439c-146">Běžným účelem pro seskupení řádků je k oddělení řádků zvláštní účely, jako je například název, záhlaví a zápatí řádků, od primární obsah obsažen v tabulce.</span><span class="sxs-lookup"><span data-stu-id="5439c-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="5439c-147">Následující příklad používá [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] definovat tabulku s řádky upravený záhlaví a zápatí.</span><span class="sxs-lookup"><span data-stu-id="5439c-147">The following example uses [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="5439c-148">Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="5439c-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="5439c-149">![Snímek obrazovky: Skupiny řádků tabulky](./media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="5439c-149">![Screenshot: Table row groups](./media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a><span data-ttu-id="5439c-150">Priorita vykreslení na pozadí</span><span class="sxs-lookup"><span data-stu-id="5439c-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="5439c-151">Vykreslení elementů tabulky v následujícím pořadí (z seřazené od nejnižší po nejvyšší).</span><span class="sxs-lookup"><span data-stu-id="5439c-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="5439c-152">Toto pořadí nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="5439c-152">This order cannot be changed.</span></span> <span data-ttu-id="5439c-153">Není třeba žádná vlastnost "Pořadí Z-order" pro tyto elementy, které můžete použít k přepsání této stanovené pořadí.</span><span class="sxs-lookup"><span data-stu-id="5439c-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="5439c-154">Zvažte následující příklad, který definuje barvy pozadí pro každý z těchto elementů v tabulce.</span><span class="sxs-lookup"><span data-stu-id="5439c-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="5439c-155">Následující obrázek ukazuje, jak v tomto příkladu vykreslí (pouze barvy pozadí zobrazení).</span><span class="sxs-lookup"><span data-stu-id="5439c-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="5439c-156">![Snímek obrazovky: Tabulky z&#45;pořadí](./media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="5439c-156">![Screenshot: Table z&#45;order](./media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="5439c-157">Pokrývání uzlů řádky nebo sloupce</span><span class="sxs-lookup"><span data-stu-id="5439c-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="5439c-158">Buňky tabulky může nakonfigurovat tak, aby span pomocí několika řádků nebo sloupců <xref:System.Windows.Documents.TableCell.RowSpan%2A> nebo <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> atributů.</span><span class="sxs-lookup"><span data-stu-id="5439c-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="5439c-159">Podívejte se na následující příklad, ve kterém buňky zahrnuje tři sloupce.</span><span class="sxs-lookup"><span data-stu-id="5439c-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="5439c-160">Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="5439c-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="5439c-161">![Snímek obrazovky: Pokrývání uzlů všechny tři sloupce buňky](./media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="5439c-161">![Screenshot: Cell spanning all three columns](./media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a><span data-ttu-id="5439c-162">Vytváření tabulky s kódem</span><span class="sxs-lookup"><span data-stu-id="5439c-162">Building a Table With Code</span></span>  
 <span data-ttu-id="5439c-163">Následující příklady ukazují, jak prostřednictvím kódu programu vytvořit <xref:System.Windows.Documents.Table> a jeho naplnění obsah.</span><span class="sxs-lookup"><span data-stu-id="5439c-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="5439c-164">Obsah tabulky jsou rozdělených do pěti řádcích (reprezentované <xref:System.Windows.Documents.TableRow> objekty obsažené v <xref:System.Windows.Documents.Table.RowGroups%2A> objekt) a šest sloupců (reprezentované <xref:System.Windows.Documents.TableColumn> objekty).</span><span class="sxs-lookup"><span data-stu-id="5439c-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="5439c-165">Řádky se používají pro účely jiné prezentace, včetně titulní řádek určený pro titulek celou tabulku popisující sloupce dat v tabulce Řádek záhlaví a řádek zápatí se souhrnnými informacemi.</span><span class="sxs-lookup"><span data-stu-id="5439c-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="5439c-166">Všimněte si, že pojem "title", "záhlaví" a "zápatí" řádek nepatří do tabulky; Jedná se o jednoduše řádky s různými charakteristikami.</span><span class="sxs-lookup"><span data-stu-id="5439c-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="5439c-167">Buňky tabulky obsahují skutečný obsah, který se může skládat z textu, obrázků nebo téměř jakýkoli jiný [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="5439c-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="5439c-168">První, <xref:System.Windows.Documents.FlowDocument> se vytvoří na hostitele <xref:System.Windows.Documents.Table>a nové <xref:System.Windows.Documents.Table> je vytvořen a přidán do obsahu <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="5439c-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="5439c-169">Dále šest <xref:System.Windows.Documents.TableColumn> objekty jsou vytvořen a přidán do tabulky <xref:System.Windows.Documents.Table.Columns%2A> kolekce s některé aplikované formátování.</span><span class="sxs-lookup"><span data-stu-id="5439c-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5439c-170">Všimněte si, že v tabulce <xref:System.Windows.Documents.Table.Columns%2A> kolekce používá standardní indexování od nuly.</span><span class="sxs-lookup"><span data-stu-id="5439c-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="5439c-171">Titulní řádek v dalším kroku je vytvořen a přidán do tabulky s některé aplikované formátování.</span><span class="sxs-lookup"><span data-stu-id="5439c-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="5439c-172">Titulní řádek se stane, tak, aby obsahovala jedinou buňku, která překlenuje všechny šest sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="5439c-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="5439c-173">V dalším kroku řádek záhlaví je vytvořen a přidán do tabulky a buňky v řádku záhlaví jsou vytvořeny a naplněny s obsahem.</span><span class="sxs-lookup"><span data-stu-id="5439c-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="5439c-174">V dalším kroku řádků dat je vytvořen a přidán do tabulky a buňky v tomto řádku jsou vytvořeny a naplněny s obsahem.</span><span class="sxs-lookup"><span data-stu-id="5439c-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="5439c-175">Vytváření tento řádek je podobný sestavování řádek záhlaví s mírně odlišné formátování.</span><span class="sxs-lookup"><span data-stu-id="5439c-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="5439c-176">Nakonec řádek zápatí vytvořili, přidat a ve formátu.</span><span class="sxs-lookup"><span data-stu-id="5439c-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="5439c-177">V zápatí je uvedené jako titulní řádek obsahuje jedinou buňku, která překlenuje všechny šest sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="5439c-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="5439c-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5439c-178">See also</span></span>

- [<span data-ttu-id="5439c-179">Přehled toku dokumentů</span><span class="sxs-lookup"><span data-stu-id="5439c-179">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="5439c-180">Definice tabulky pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="5439c-180">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="5439c-181">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="5439c-181">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="5439c-182">Použití elementů obsahu toku</span><span class="sxs-lookup"><span data-stu-id="5439c-182">Use Flow Content Elements</span></span>](how-to-use-flow-content-elements.md)
