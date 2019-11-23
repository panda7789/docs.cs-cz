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
# <a name="table-overview"></a><span data-ttu-id="cae68-102">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="cae68-102">Table Overview</span></span>
<span data-ttu-id="cae68-103"><xref:System.Windows.Documents.Table> je prvek na úrovni bloku, který podporuje prezentaci na základě mřížky obsahu dokumentu toku.</span><span class="sxs-lookup"><span data-stu-id="cae68-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="cae68-104">Flexibilita tohoto prvku je velmi užitečná, ale také usnadňuje pochopení a používání správně.</span><span class="sxs-lookup"><span data-stu-id="cae68-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="cae68-105">Toto téma obsahuje následující části.</span><span class="sxs-lookup"><span data-stu-id="cae68-105">This topic contains the following sections.</span></span>  
  
- [<span data-ttu-id="cae68-106">Základy tabulek</span><span class="sxs-lookup"><span data-stu-id="cae68-106">Table Basics</span></span>](#table_basics)  
  
- [<span data-ttu-id="cae68-107">Jak je tabulka odlišná pro mřížku?</span><span class="sxs-lookup"><span data-stu-id="cae68-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
- [<span data-ttu-id="cae68-108">Základní struktura tabulky</span><span class="sxs-lookup"><span data-stu-id="cae68-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
- [<span data-ttu-id="cae68-109">Zahrnutí tabulky</span><span class="sxs-lookup"><span data-stu-id="cae68-109">Table Containment</span></span>](#table_containment)  
  
- [<span data-ttu-id="cae68-110">Seskupení řádků</span><span class="sxs-lookup"><span data-stu-id="cae68-110">Row Groupings</span></span>](#row_groupings)  
  
- [<span data-ttu-id="cae68-111">Priorita vykreslování na pozadí</span><span class="sxs-lookup"><span data-stu-id="cae68-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
- [<span data-ttu-id="cae68-112">Pokrývání řádků nebo sloupců</span><span class="sxs-lookup"><span data-stu-id="cae68-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
- [<span data-ttu-id="cae68-113">Vytvoření tabulky s kódem</span><span class="sxs-lookup"><span data-stu-id="cae68-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
- <span data-ttu-id="cae68-114">[Související témata]</span><span class="sxs-lookup"><span data-stu-id="cae68-114">[Related Topics]</span></span> 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a><span data-ttu-id="cae68-115">Základy tabulek</span><span class="sxs-lookup"><span data-stu-id="cae68-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="cae68-116">Jak je tabulka odlišná pro mřížku?</span><span class="sxs-lookup"><span data-stu-id="cae68-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="cae68-117"><xref:System.Windows.Documents.Table> a <xref:System.Windows.Controls.Grid> sdílet některé běžné funkce, ale každá z nich nejlépe vyhovuje různým scénářům.</span><span class="sxs-lookup"><span data-stu-id="cae68-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="cae68-118"><xref:System.Windows.Documents.Table> je navržený pro použití v rámci obsahu toku (Další informace o obsahu toku najdete v tématu [Přehled dokumentů flowu](flow-document-overview.md) ).</span><span class="sxs-lookup"><span data-stu-id="cae68-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="cae68-119">Mřížky se nejlépe používají ve formulářích (v podstatě kdekoli mimo obsah toku).</span><span class="sxs-lookup"><span data-stu-id="cae68-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="cae68-120">V rámci <xref:System.Windows.Documents.FlowDocument><xref:System.Windows.Documents.Table> podporuje chování toku obsahu, jako jsou stránkování, přetékání sloupců a výběr obsahu, zatímco <xref:System.Windows.Controls.Grid> ne.</span><span class="sxs-lookup"><span data-stu-id="cae68-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="cae68-121"><xref:System.Windows.Controls.Grid> na druhé straně se nejlépe využije mimo <xref:System.Windows.Documents.FlowDocument> z mnoha důvodů, včetně <xref:System.Windows.Controls.Grid> přidá prvky založené na indexu řádků a sloupců, <xref:System.Windows.Documents.Table> ne.</span><span class="sxs-lookup"><span data-stu-id="cae68-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="cae68-122">Element <xref:System.Windows.Controls.Grid> umožňuje vrstvení podřízeného obsahu, což umožňuje, aby v jedné "buňce" existoval více než jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="cae68-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="cae68-123"><xref:System.Windows.Documents.Table> nepodporuje vrstvení.</span><span class="sxs-lookup"><span data-stu-id="cae68-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="cae68-124">Podřízené prvky <xref:System.Windows.Controls.Grid> mohou být absolutně umístěny relativně k oblasti jejich hranic "buňka".</span><span class="sxs-lookup"><span data-stu-id="cae68-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="cae68-125"><xref:System.Windows.Documents.Table> tuto funkci nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="cae68-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="cae68-126">Nakonec <xref:System.Windows.Controls.Grid> vyžaduje méně prostředků, a proto byste měli <xref:System.Windows.Documents.Table> zvážit použití <xref:System.Windows.Controls.Grid> ke zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="cae68-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a><span data-ttu-id="cae68-127">Základní struktura tabulky</span><span class="sxs-lookup"><span data-stu-id="cae68-127">Basic Table Structure</span></span>  
 <span data-ttu-id="cae68-128"><xref:System.Windows.Documents.Table> poskytuje prezentaci založenou na mřížce sestávající ze sloupců (reprezentovaných <xref:System.Windows.Documents.TableColumn> prvky) a řádků (reprezentovaných prvky <xref:System.Windows.Documents.TableRow>).</span><span class="sxs-lookup"><span data-stu-id="cae68-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="cae68-129">prvky <xref:System.Windows.Documents.TableColumn> neobsahují hostování obsahu; jednoduše definují sloupce a charakteristiky sloupců.</span><span class="sxs-lookup"><span data-stu-id="cae68-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="cae68-130">prvky <xref:System.Windows.Documents.TableRow> musí být hostovány v <xref:System.Windows.Documents.TableRowGroup> elementu, který definuje seskupení řádků pro tabulku.</span><span class="sxs-lookup"><span data-stu-id="cae68-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="cae68-131">prvky <xref:System.Windows.Documents.TableCell>, které obsahují skutečný obsah, který má být prezentován tabulkou, musí být hostovány v <xref:System.Windows.Documents.TableRow> elementu.</span><span class="sxs-lookup"><span data-stu-id="cae68-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="cae68-132"><xref:System.Windows.Documents.TableCell> může obsahovat pouze prvky, které jsou odvozeny z <xref:System.Windows.Documents.Block>.</span><span class="sxs-lookup"><span data-stu-id="cae68-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="cae68-133">Platné podřízené prvky pro <xref:System.Windows.Documents.TableCell> zahrnují.</span><span class="sxs-lookup"><span data-stu-id="cae68-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <span data-ttu-id="cae68-134">prvky <xref:System.Windows.Documents.TableCell> nemůžou přímo hostovat textový obsah.</span><span class="sxs-lookup"><span data-stu-id="cae68-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="cae68-135">Další informace o pravidlech omezení pro prvky obsahu toku, jako je <xref:System.Windows.Documents.TableCell>, naleznete v tématu [Flow Flow Overview](flow-document-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cae68-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](flow-document-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cae68-136"><xref:System.Windows.Documents.Table> je podobná <xref:System.Windows.Controls.Grid>mu prvku, ale má více možností, a proto vyžaduje větší nároky na prostředky.</span><span class="sxs-lookup"><span data-stu-id="cae68-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="cae68-137">V následujícím příkladu je definována Jednoduchá tabulka 2 x 3 s XAML.</span><span class="sxs-lookup"><span data-stu-id="cae68-137">The following example defines a simple 2 x 3 table with XAML.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="cae68-138">Následující obrázek ukazuje, jak tento příklad vykresluje.</span><span class="sxs-lookup"><span data-stu-id="cae68-138">The following figure shows how this example renders.</span></span>  
  
 ![Snímek obrazovky, který ukazuje, jak vykreslí základní tabulka](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a><span data-ttu-id="cae68-140">Zahrnutí tabulky</span><span class="sxs-lookup"><span data-stu-id="cae68-140">Table Containment</span></span>  
 <span data-ttu-id="cae68-141"><xref:System.Windows.Documents.Table> je odvozen z prvku <xref:System.Windows.Documents.Block> a dodržuje společná pravidla pro <xref:System.Windows.Documents.Block> prvků na úrovni.</span><span class="sxs-lookup"><span data-stu-id="cae68-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="cae68-142">Element <xref:System.Windows.Documents.Table> může být obsažený v některém z následujících elementů:</span><span class="sxs-lookup"><span data-stu-id="cae68-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a><span data-ttu-id="cae68-143">Seskupení řádků</span><span class="sxs-lookup"><span data-stu-id="cae68-143">Row Groupings</span></span>  
 <span data-ttu-id="cae68-144">Element <xref:System.Windows.Documents.TableRowGroup> poskytuje způsob, jak v tabulce libovolně seskupovat řádky; Každý řádek v tabulce musí patřit do seskupení řádků.</span><span class="sxs-lookup"><span data-stu-id="cae68-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="cae68-145">Řádky v rámci skupiny řádků často sdílejí běžný záměr a můžou být ve stylu jako skupina.</span><span class="sxs-lookup"><span data-stu-id="cae68-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="cae68-146">Běžné použití pro seskupení řádků je samostatné řádky, jako je název, hlavička a řádky zápatí, od primárního obsahu obsaženého v tabulce.</span><span class="sxs-lookup"><span data-stu-id="cae68-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="cae68-147">Následující příklad používá XAML k definování tabulky se stylem řádky záhlaví a zápatí.</span><span class="sxs-lookup"><span data-stu-id="cae68-147">The following example uses XAML to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="cae68-148">Následující obrázek ukazuje, jak tento příklad vykresluje.</span><span class="sxs-lookup"><span data-stu-id="cae68-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="cae68-149">![Snímek obrazovky: Table_RowGroups skupiny řádků tabulky](./media/table-rowgroups.png "")</span><span class="sxs-lookup"><span data-stu-id="cae68-149">![Screenshot: Table row groups](./media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a><span data-ttu-id="cae68-150">Priorita vykreslování na pozadí</span><span class="sxs-lookup"><span data-stu-id="cae68-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="cae68-151">Prvky tabulky se vykreslují v následujícím pořadí (pořadí z od nejnižší po nejvyšší).</span><span class="sxs-lookup"><span data-stu-id="cae68-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="cae68-152">Tuto objednávku nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="cae68-152">This order cannot be changed.</span></span> <span data-ttu-id="cae68-153">Například neexistuje žádná vlastnost "Z-order" pro tyto prvky, které lze použít k přepsání tohoto navázaného pořadí.</span><span class="sxs-lookup"><span data-stu-id="cae68-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="cae68-154">Vezměte v úvahu následující příklad, který definuje barvy pozadí pro každý z těchto prvků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="cae68-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="cae68-155">Následující obrázek ukazuje, jak tento příklad vykresluje (zobrazí pouze barvy pozadí).</span><span class="sxs-lookup"><span data-stu-id="cae68-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="cae68-156">![Snímek obrazovky:&#45;Table_ZOrder pořadí z tabulky](./media/table-zorder.png "")</span><span class="sxs-lookup"><span data-stu-id="cae68-156">![Screenshot: Table z&#45;order](./media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="cae68-157">Pokrývání řádků nebo sloupců</span><span class="sxs-lookup"><span data-stu-id="cae68-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="cae68-158">Buňky tabulky můžou být nakonfigurované tak, aby pokrývají více řádků nebo sloupců pomocí atributů <xref:System.Windows.Documents.TableCell.RowSpan%2A> nebo <xref:System.Windows.Documents.TableCell.ColumnSpan%2A>, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cae68-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="cae68-159">Vezměte v úvahu následující příklad, ve kterém buňka zahrnuje tři sloupce.</span><span class="sxs-lookup"><span data-stu-id="cae68-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="cae68-160">Následující obrázek ukazuje, jak tento příklad vykresluje.</span><span class="sxs-lookup"><span data-stu-id="cae68-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="cae68-161">![Snímek obrazovky: buňky zahrnující všechny tři sloupce](./media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="cae68-161">![Screenshot: Cell spanning all three columns](./media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a><span data-ttu-id="cae68-162">Vytvoření tabulky s kódem</span><span class="sxs-lookup"><span data-stu-id="cae68-162">Building a Table With Code</span></span>  
 <span data-ttu-id="cae68-163">Následující příklady ukazují, jak programově vytvořit <xref:System.Windows.Documents.Table> a naplnit ho obsahem.</span><span class="sxs-lookup"><span data-stu-id="cae68-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="cae68-164">Obsah tabulky se rozdělí na pět řádků (reprezentovaných <xref:System.Windows.Documents.TableRow> objekty obsaženými v objektu <xref:System.Windows.Documents.Table.RowGroups%2A>) a šesti sloupcích (reprezentované objekty <xref:System.Windows.Documents.TableColumn>).</span><span class="sxs-lookup"><span data-stu-id="cae68-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="cae68-165">Řádky se používají pro různé účely prezentace, včetně řádku názvu, který je určený k nadpisu celé tabulky, řádku záhlaví, který popisuje sloupce dat v tabulce a řádek zápatí se souhrnnými informacemi.</span><span class="sxs-lookup"><span data-stu-id="cae68-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="cae68-166">Všimněte si, že pojem "title", "header" a "Foot" řádky nejsou podstatou tabulky; Jedná se o jednoduché řádky s různými charakteristikami.</span><span class="sxs-lookup"><span data-stu-id="cae68-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="cae68-167">Buňky tabulky obsahují skutečný obsah, který se může skládat z textu, obrázků nebo téměř jakéhokoli jiného prvku [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cae68-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="cae68-168">Nejprve se vytvoří <xref:System.Windows.Documents.FlowDocument> pro hostování <xref:System.Windows.Documents.Table>a vytvoří se nový <xref:System.Windows.Documents.Table>, který se přidá k obsahu <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="cae68-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="cae68-169">V dalším kroku se vytvoří šest <xref:System.Windows.Documents.TableColumn> objektů a přidají se do kolekce <xref:System.Windows.Documents.Table.Columns%2A> tabulky s použitím některých formátování.</span><span class="sxs-lookup"><span data-stu-id="cae68-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cae68-170">Všimněte si, že kolekce <xref:System.Windows.Documents.Table.Columns%2A> tabulky používá standardní indexování založené na nule.</span><span class="sxs-lookup"><span data-stu-id="cae68-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="cae68-171">V dalším kroku se vytvoří řádek s nadpisem a přidá se do tabulky s některým použitým formátováním.</span><span class="sxs-lookup"><span data-stu-id="cae68-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="cae68-172">Řádek nadpisu obsahuje jednu buňku, která zahrnuje všechny šest sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="cae68-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="cae68-173">V dalším kroku se vytvoří řádek záhlaví a přidá se do tabulky a buňky v řádku záhlaví se vytvoří a naplní se obsahem.</span><span class="sxs-lookup"><span data-stu-id="cae68-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="cae68-174">V dalším kroku se vytvoří řádek pro data a přidají se do tabulky a buňky v tomto řádku se vytvoří a naplní se obsahem.</span><span class="sxs-lookup"><span data-stu-id="cae68-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="cae68-175">Sestavování tohoto řádku se podobá vytvoření řádku záhlaví s mírně odlišným formátováním.</span><span class="sxs-lookup"><span data-stu-id="cae68-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="cae68-176">Nakonec se vytvoří, přidá a naformátuje řádek zápatí.</span><span class="sxs-lookup"><span data-stu-id="cae68-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="cae68-177">Podobně jako u řádku nadpisu obsahuje zápatí jedinou buňku, která zahrnuje všechny šest sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="cae68-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="cae68-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cae68-178">See also</span></span>

- [<span data-ttu-id="cae68-179">Přehled toku dokumentů</span><span class="sxs-lookup"><span data-stu-id="cae68-179">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="cae68-180">Definice tabulky pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="cae68-180">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="cae68-181">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="cae68-181">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="cae68-182">Použití elementů obsahu toku</span><span class="sxs-lookup"><span data-stu-id="cae68-182">Use Flow Content Elements</span></span>](how-to-use-flow-content-elements.md)
