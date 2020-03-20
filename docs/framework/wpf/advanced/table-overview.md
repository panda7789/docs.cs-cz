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
# <a name="table-overview"></a><span data-ttu-id="c6355-102">Přehled tabulek</span><span class="sxs-lookup"><span data-stu-id="c6355-102">Table Overview</span></span>
<span data-ttu-id="c6355-103"><xref:System.Windows.Documents.Table>je prvek na úrovni bloku, který podporuje prezentaci obsahu dokumentu Flow na základě mřížky.</span><span class="sxs-lookup"><span data-stu-id="c6355-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="c6355-104">Flexibilita tohoto prvku je velmi užitečná, ale také ztěžuje pochopení a správné používání.</span><span class="sxs-lookup"><span data-stu-id="c6355-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="c6355-105">Toto téma obsahuje tyto části:</span><span class="sxs-lookup"><span data-stu-id="c6355-105">This topic contains the following sections.</span></span>  
  
- [<span data-ttu-id="c6355-106">Základy tabulky</span><span class="sxs-lookup"><span data-stu-id="c6355-106">Table Basics</span></span>](#table_basics)  
  
- [<span data-ttu-id="c6355-107">Jak se tabulka liší pak Grid?</span><span class="sxs-lookup"><span data-stu-id="c6355-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
- [<span data-ttu-id="c6355-108">Základní struktura tabulky</span><span class="sxs-lookup"><span data-stu-id="c6355-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
- [<span data-ttu-id="c6355-109">Uzavření tabulky</span><span class="sxs-lookup"><span data-stu-id="c6355-109">Table Containment</span></span>](#table_containment)  
  
- [<span data-ttu-id="c6355-110">Seskupení řádků</span><span class="sxs-lookup"><span data-stu-id="c6355-110">Row Groupings</span></span>](#row_groupings)  
  
- [<span data-ttu-id="c6355-111">Priorita vykreslování na pozadí</span><span class="sxs-lookup"><span data-stu-id="c6355-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
- [<span data-ttu-id="c6355-112">Překrývání řádků nebo sloupců</span><span class="sxs-lookup"><span data-stu-id="c6355-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
- [<span data-ttu-id="c6355-113">Vytváření tabulky s kódem</span><span class="sxs-lookup"><span data-stu-id="c6355-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
- <span data-ttu-id="c6355-114">[Příbuzná témata]</span><span class="sxs-lookup"><span data-stu-id="c6355-114">[Related Topics]</span></span>
  
<a name="table_basics"></a>
## <a name="table-basics"></a><span data-ttu-id="c6355-115">Základy tabulky</span><span class="sxs-lookup"><span data-stu-id="c6355-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="c6355-116">Jak se tabulka liší pak Grid?</span><span class="sxs-lookup"><span data-stu-id="c6355-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="c6355-117"><xref:System.Windows.Documents.Table>a <xref:System.Windows.Controls.Grid> sdílet některé běžné funkce, ale každý je nejvhodnější pro různé scénáře.</span><span class="sxs-lookup"><span data-stu-id="c6355-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="c6355-118">A <xref:System.Windows.Documents.Table> je určen pro použití v rámci obsahu toku (viz [Přehled toku dokumentu](flow-document-overview.md) pro další informace o obsahu toku).</span><span class="sxs-lookup"><span data-stu-id="c6355-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="c6355-119">Mřížky se nejlépe používají uvnitř formulářů (v podstatě kdekoli mimo obsah toku).</span><span class="sxs-lookup"><span data-stu-id="c6355-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="c6355-120">V <xref:System.Windows.Documents.FlowDocument>rámci <xref:System.Windows.Documents.Table> , podporuje chování obsahu toku, jako je stránkování, přeformátování sloupců a výběr obsahu, zatímco <xref:System.Windows.Controls.Grid> a není.</span><span class="sxs-lookup"><span data-stu-id="c6355-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="c6355-121">A <xref:System.Windows.Controls.Grid> na druhé straně se nejlépe <xref:System.Windows.Documents.FlowDocument> používá mimo <xref:System.Windows.Controls.Grid> z mnoha důvodů, včetně <xref:System.Windows.Documents.Table> přidá prvky založené na řádku a sloupec index, není.</span><span class="sxs-lookup"><span data-stu-id="c6355-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="c6355-122">Prvek <xref:System.Windows.Controls.Grid> umožňuje vrstvení podřízeného obsahu, což umožňuje více než jeden prvek existovat v rámci jedné "buňky".</span><span class="sxs-lookup"><span data-stu-id="c6355-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="c6355-123"><xref:System.Windows.Documents.Table>nepodporuje vrstvení.</span><span class="sxs-lookup"><span data-stu-id="c6355-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="c6355-124">Podřízené <xref:System.Windows.Controls.Grid> prvky může být absolutně umístěn vzhledem k oblasti jejich "buňky" hranice.</span><span class="sxs-lookup"><span data-stu-id="c6355-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="c6355-125"><xref:System.Windows.Documents.Table>nepodporuje tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="c6355-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="c6355-126">Nakonec vyžaduje <xref:System.Windows.Controls.Grid> méně prostředků <xref:System.Windows.Documents.Table> pak tak <xref:System.Windows.Controls.Grid> zvážit použití ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="c6355-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>
### <a name="basic-table-structure"></a><span data-ttu-id="c6355-127">Základní struktura tabulky</span><span class="sxs-lookup"><span data-stu-id="c6355-127">Basic Table Structure</span></span>  
 <span data-ttu-id="c6355-128"><xref:System.Windows.Documents.Table>poskytuje prezentaci založenou na mřížce skládající se ze sloupců (reprezentované <xref:System.Windows.Documents.TableColumn> prvky) a řádků (reprezentované <xref:System.Windows.Documents.TableRow> prvky).</span><span class="sxs-lookup"><span data-stu-id="c6355-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="c6355-129"><xref:System.Windows.Documents.TableColumn>prvky nehostují obsah; jednoduše definují sloupce a charakteristiky sloupců.</span><span class="sxs-lookup"><span data-stu-id="c6355-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="c6355-130"><xref:System.Windows.Documents.TableRow>prvky musí být <xref:System.Windows.Documents.TableRowGroup> hostovány v elementu, který definuje seskupení řádků pro tabulku.</span><span class="sxs-lookup"><span data-stu-id="c6355-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="c6355-131"><xref:System.Windows.Documents.TableCell>prvky, které obsahují skutečný obsah, který má být předložen <xref:System.Windows.Documents.TableRow> v tabulce, musí být hostovány v prvku.</span><span class="sxs-lookup"><span data-stu-id="c6355-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="c6355-132"><xref:System.Windows.Documents.TableCell>mohou obsahovat pouze <xref:System.Windows.Documents.Block>prvky, které jsou odvozeny z .</span><span class="sxs-lookup"><span data-stu-id="c6355-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="c6355-133">Platné podřízené <xref:System.Windows.Documents.TableCell> prvky pro include.</span><span class="sxs-lookup"><span data-stu-id="c6355-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <span data-ttu-id="c6355-134"><xref:System.Windows.Documents.TableCell>prvky nemusí přímo hostovat textový obsah.</span><span class="sxs-lookup"><span data-stu-id="c6355-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="c6355-135">Další informace o pravidlech uzavření pro <xref:System.Windows.Documents.TableCell>prvky obsahu toku, jako je , naleznete [v tématu Přehled dokumentu toku](flow-document-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c6355-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](flow-document-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6355-136"><xref:System.Windows.Documents.Table>je podobný <xref:System.Windows.Controls.Grid> prvku, ale má více možností a proto vyžaduje větší režii prostředků.</span><span class="sxs-lookup"><span data-stu-id="c6355-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="c6355-137">Následující příklad definuje jednoduchou tabulku 2 x 3 s XAML.</span><span class="sxs-lookup"><span data-stu-id="c6355-137">The following example defines a simple 2 x 3 table with XAML.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="c6355-138">Následující obrázek ukazuje, jak se tento příklad vykresluje.</span><span class="sxs-lookup"><span data-stu-id="c6355-138">The following figure shows how this example renders.</span></span>  
  
 ![Snímek obrazovky, který ukazuje, jak se vykresluje základní tabulka.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>
### <a name="table-containment"></a><span data-ttu-id="c6355-140">Uzavření tabulky</span><span class="sxs-lookup"><span data-stu-id="c6355-140">Table Containment</span></span>  
 <span data-ttu-id="c6355-141"><xref:System.Windows.Documents.Table>odvozuje <xref:System.Windows.Documents.Block> z prvku a dodržuje společná <xref:System.Windows.Documents.Block> pravidla pro prvky úrovně.</span><span class="sxs-lookup"><span data-stu-id="c6355-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="c6355-142">Prvek <xref:System.Windows.Documents.Table> může být obsažen v některém z těchto prvků:</span><span class="sxs-lookup"><span data-stu-id="c6355-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>
### <a name="row-groupings"></a><span data-ttu-id="c6355-143">Seskupení řádků</span><span class="sxs-lookup"><span data-stu-id="c6355-143">Row Groupings</span></span>  
 <span data-ttu-id="c6355-144">Prvek <xref:System.Windows.Documents.TableRowGroup> poskytuje způsob, jak libovolně seskupit řádky v rámci tabulky; každý řádek v tabulce musí patřit do seskupení řádků.</span><span class="sxs-lookup"><span data-stu-id="c6355-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="c6355-145">Řádky ve skupině řádků často sdílejí společný záměr a mohou být stylizovány jako skupina.</span><span class="sxs-lookup"><span data-stu-id="c6355-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="c6355-146">Pro seskupení řádků se běžně používá oddělení řádků pro speciální účely, například řádků nadpisů, záhlaví a zápatí, od primárního obsahu obsaženého v tabulce.</span><span class="sxs-lookup"><span data-stu-id="c6355-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="c6355-147">Následující příklad používá XAML k definování tabulky se stylizovanými řádky záhlaví a zápatí.</span><span class="sxs-lookup"><span data-stu-id="c6355-147">The following example uses XAML to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="c6355-148">Následující obrázek ukazuje, jak se tento příklad vykresluje.</span><span class="sxs-lookup"><span data-stu-id="c6355-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="c6355-149">![Snímek obrazovky: Skupiny řádků tabulky](./media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="c6355-149">![Screenshot: Table row groups](./media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>
### <a name="background-rendering-precedence"></a><span data-ttu-id="c6355-150">Priorita vykreslování na pozadí</span><span class="sxs-lookup"><span data-stu-id="c6355-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="c6355-151">Prvky tabulky se vykreslují v následujícím pořadí (pořadí vykreslování od nejnižší po nejvyšší).</span><span class="sxs-lookup"><span data-stu-id="c6355-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="c6355-152">Toto pořadí nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="c6355-152">This order cannot be changed.</span></span> <span data-ttu-id="c6355-153">Například neexistuje žádná vlastnost "Pořadí vykreslovat" pro tyto prvky, které můžete použít k přepsání tohoto zavedeného pořadí.</span><span class="sxs-lookup"><span data-stu-id="c6355-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="c6355-154">Vezměme si následující příklad, který definuje barvy pozadí pro každý z těchto prvků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="c6355-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="c6355-155">Následující obrázek ukazuje, jak se tento příklad vykresluje (zobrazuje pouze barvy pozadí).</span><span class="sxs-lookup"><span data-stu-id="c6355-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="c6355-156">![Snímek obrazovky: Tabulka z&#45;pořadí](./media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="c6355-156">![Screenshot: Table z&#45;order](./media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="c6355-157">Překrývání řádků nebo sloupců</span><span class="sxs-lookup"><span data-stu-id="c6355-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="c6355-158">Buňky tabulky mohou být nakonfigurovány tak, <xref:System.Windows.Documents.TableCell.RowSpan%2A> <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> aby se rozprostíraly na více řádků nebo sloupců pomocí atributů nebo.</span><span class="sxs-lookup"><span data-stu-id="c6355-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="c6355-159">Vezměme si následující příklad, ve kterém buňka pokrývá tři sloupce.</span><span class="sxs-lookup"><span data-stu-id="c6355-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="c6355-160">Následující obrázek ukazuje, jak se tento příklad vykresluje.</span><span class="sxs-lookup"><span data-stu-id="c6355-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="c6355-161">![Snímek obrazovky: Buňka zahrnující všechny tři sloupce](./media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="c6355-161">![Screenshot: Cell spanning all three columns](./media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>
## <a name="building-a-table-with-code"></a><span data-ttu-id="c6355-162">Vytváření tabulky s kódem</span><span class="sxs-lookup"><span data-stu-id="c6355-162">Building a Table With Code</span></span>  
 <span data-ttu-id="c6355-163">Následující příklady ukazují, jak programově <xref:System.Windows.Documents.Table> vytvořit a naplnit obsahem.</span><span class="sxs-lookup"><span data-stu-id="c6355-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="c6355-164">Obsah tabulky je rozdělen do pěti řádků (reprezentovaných objekty obsaženými <xref:System.Windows.Documents.TableRow> v objektu) <xref:System.Windows.Documents.Table.RowGroups%2A> a šesti sloupcích (reprezentovaných objekty). <xref:System.Windows.Documents.TableColumn></span><span class="sxs-lookup"><span data-stu-id="c6355-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="c6355-165">Řádky se používají pro různé účely prezentace, včetně řádku nadpisu určeného k označení celé tabulky, řádku záhlaví popisujícího sloupce dat v tabulce a řádku zápatí se souhrnnými informacemi.</span><span class="sxs-lookup"><span data-stu-id="c6355-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="c6355-166">Všimněte si, že pojem "název", "záhlaví" a "zápatí" řádky nejsou vlastní tabulce; jedná se jednoduše o řádky s různými vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="c6355-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="c6355-167">Buňky tabulky obsahují skutečný obsah, který může být tvořen textem, obrázky nebo téměř jakýmkoli jiným [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] prvkem.</span><span class="sxs-lookup"><span data-stu-id="c6355-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="c6355-168">Nejprve <xref:System.Windows.Documents.FlowDocument> a je vytvořen <xref:System.Windows.Documents.Table>pro hostování <xref:System.Windows.Documents.Table> , a nový je <xref:System.Windows.Documents.FlowDocument>vytvořen a přidán do obsahu .</span><span class="sxs-lookup"><span data-stu-id="c6355-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="c6355-169">Dále šest <xref:System.Windows.Documents.TableColumn> objektů jsou vytvořeny a přidány <xref:System.Windows.Documents.Table.Columns%2A> do kolekce tabulky, s některé formátování použít.</span><span class="sxs-lookup"><span data-stu-id="c6355-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6355-170">Všimněte si, <xref:System.Windows.Documents.Table.Columns%2A> že kolekce tabulky používá standardní indexování s nulou.</span><span class="sxs-lookup"><span data-stu-id="c6355-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="c6355-171">Dále je vytvořen řádek nadpisu a přidán do tabulky s použitým formátováním.</span><span class="sxs-lookup"><span data-stu-id="c6355-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="c6355-172">Řádek nadpisu obsahuje jednu buňku, která pokrývá všech šest sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="c6355-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="c6355-173">Dále je vytvořen řádek záhlaví a přidán do tabulky a buňky v řádku záhlaví jsou vytvořeny a naplněny obsahem.</span><span class="sxs-lookup"><span data-stu-id="c6355-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="c6355-174">Dále je vytvořen řádek pro data a přidán do tabulky a buňky v tomto řádku jsou vytvořeny a naplněny obsahem.</span><span class="sxs-lookup"><span data-stu-id="c6355-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="c6355-175">Vytvoření tohoto řádku je podobné vytváření řádku záhlaví s mírně odlišným formátováním.</span><span class="sxs-lookup"><span data-stu-id="c6355-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="c6355-176">Nakonec je vytvořen, přidán a formátován řádek zápatí.</span><span class="sxs-lookup"><span data-stu-id="c6355-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="c6355-177">Podobně jako titulní řádek obsahuje zápatí jednu buňku, která pokrývá všech šest sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="c6355-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="c6355-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6355-178">See also</span></span>

- [<span data-ttu-id="c6355-179">Přehled toku dokumentů</span><span class="sxs-lookup"><span data-stu-id="c6355-179">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="c6355-180">Definování tabulky pomocí jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="c6355-180">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="c6355-181">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="c6355-181">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="c6355-182">Použití elementů obsahu toku</span><span class="sxs-lookup"><span data-stu-id="c6355-182">Use Flow Content Elements</span></span>](how-to-use-flow-content-elements.md)
