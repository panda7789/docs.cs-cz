---
title: "Přehled tabulky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb9edf0439c985af015d6badd11c026449a82f57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="table-overview"></a><span data-ttu-id="55ec9-102">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="55ec9-102">Table Overview</span></span>
<span data-ttu-id="55ec9-103"><xref:System.Windows.Documents.Table>je úrovně blokovém elementu, které podporuje předložení mřížky obsah dokumentu toku.</span><span class="sxs-lookup"><span data-stu-id="55ec9-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="55ec9-104">Flexibilita tohoto elementu je velmi užitečná, ale také umožňuje složitěji, pochopit a používat správně.</span><span class="sxs-lookup"><span data-stu-id="55ec9-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="55ec9-105">Toto téma obsahuje následující části.</span><span class="sxs-lookup"><span data-stu-id="55ec9-105">This topic contains the following sections.</span></span>  
  
-   [<span data-ttu-id="55ec9-106">Základní informace o tabulce</span><span class="sxs-lookup"><span data-stu-id="55ec9-106">Table Basics</span></span>](#table_basics)  
  
-   [<span data-ttu-id="55ec9-107">Jak je tabulka různých pak mřížky?</span><span class="sxs-lookup"><span data-stu-id="55ec9-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
-   [<span data-ttu-id="55ec9-108">Struktura základní tabulky</span><span class="sxs-lookup"><span data-stu-id="55ec9-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
-   [<span data-ttu-id="55ec9-109">Tabulka členství ve skupině</span><span class="sxs-lookup"><span data-stu-id="55ec9-109">Table Containment</span></span>](#table_containment)  
  
-   [<span data-ttu-id="55ec9-110">Seskupení řádků</span><span class="sxs-lookup"><span data-stu-id="55ec9-110">Row Groupings</span></span>](#row_groupings)  
  
-   [<span data-ttu-id="55ec9-111">Priorita vykreslování pozadí</span><span class="sxs-lookup"><span data-stu-id="55ec9-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
-   [<span data-ttu-id="55ec9-112">Řádky nebo sloupce</span><span class="sxs-lookup"><span data-stu-id="55ec9-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
-   [<span data-ttu-id="55ec9-113">Vytvoří tabulku s kódem</span><span class="sxs-lookup"><span data-stu-id="55ec9-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
-   <span data-ttu-id="55ec9-114">[Příbuzná témata]</span><span class="sxs-lookup"><span data-stu-id="55ec9-114">[Related Topics]</span></span> 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a><span data-ttu-id="55ec9-115">Základní informace o tabulce</span><span class="sxs-lookup"><span data-stu-id="55ec9-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="55ec9-116">Jak je tabulka různých pak mřížky?</span><span class="sxs-lookup"><span data-stu-id="55ec9-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="55ec9-117"><xref:System.Windows.Documents.Table>a <xref:System.Windows.Controls.Grid> sdílet některé běžné funkce, ale každý je nejvhodnější pro různé scénáře.</span><span class="sxs-lookup"><span data-stu-id="55ec9-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="55ec9-118">A <xref:System.Windows.Documents.Table> je určená pro použití v rámci toku obsahu (najdete v části [toku dokumentu přehled](../../../../docs/framework/wpf/advanced/flow-document-overview.md) Další informace o toku obsahu).</span><span class="sxs-lookup"><span data-stu-id="55ec9-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](../../../../docs/framework/wpf/advanced/flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="55ec9-119">Mřížky jsou nejvhodnější uvnitř forms (v podstatě kamkoli mimo toku obsahu).</span><span class="sxs-lookup"><span data-stu-id="55ec9-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="55ec9-120">V rámci <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> podporuje toku obsahu chování jako stránkování, přeformátování sloupců a výběru obsahu při <xref:System.Windows.Controls.Grid> neexistuje.</span><span class="sxs-lookup"><span data-stu-id="55ec9-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="55ec9-121">A <xref:System.Windows.Controls.Grid> na druhé straně je nejvhodnější mimo <xref:System.Windows.Documents.FlowDocument> z mnoha důvodů včetně <xref:System.Windows.Controls.Grid> přidá elementy podle řádků a sloupců index, <xref:System.Windows.Documents.Table> neexistuje.</span><span class="sxs-lookup"><span data-stu-id="55ec9-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="55ec9-122"><xref:System.Windows.Controls.Grid> Element umožňuje rozvrstvení podřízené obsahu, povolení více než jeden element existovat v jednom "buňky."</span><span class="sxs-lookup"><span data-stu-id="55ec9-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="55ec9-123"><xref:System.Windows.Documents.Table>nepodporuje rozvrstvení.</span><span class="sxs-lookup"><span data-stu-id="55ec9-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="55ec9-124">Podřízených elementů <xref:System.Windows.Controls.Grid> možné absolutně umístit relativně k oblasti hranic jejich "buňky".</span><span class="sxs-lookup"><span data-stu-id="55ec9-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="55ec9-125"><xref:System.Windows.Documents.Table>Tato funkce není podporována.</span><span class="sxs-lookup"><span data-stu-id="55ec9-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="55ec9-126">Nakonec <xref:System.Windows.Controls.Grid> vyžaduje méně prostředků pak <xref:System.Windows.Documents.Table> , zvažte použití <xref:System.Windows.Controls.Grid> ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="55ec9-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a><span data-ttu-id="55ec9-127">Struktura základní tabulky</span><span class="sxs-lookup"><span data-stu-id="55ec9-127">Basic Table Structure</span></span>  
 <span data-ttu-id="55ec9-128"><xref:System.Windows.Documents.Table>poskytuje na základě mřížky prezentace skládající se z sloupců (reprezentována <xref:System.Windows.Documents.TableColumn> prvky) a řádky (reprezentována <xref:System.Windows.Documents.TableRow> elementy).</span><span class="sxs-lookup"><span data-stu-id="55ec9-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="55ec9-129"><xref:System.Windows.Documents.TableColumn>elementy nejsou hostiteli obsahu; jednoduše definovat sloupce a vlastnosti sloupců.</span><span class="sxs-lookup"><span data-stu-id="55ec9-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="55ec9-130"><xref:System.Windows.Documents.TableRow>elementy musí být uloženy ve <xref:System.Windows.Documents.TableRowGroup> element, který definuje seskupení řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="55ec9-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="55ec9-131"><xref:System.Windows.Documents.TableCell>elementy, které obsahují skutečný obsah předávané tabulky, musí být uloženy ve <xref:System.Windows.Documents.TableRow> elementu.</span><span class="sxs-lookup"><span data-stu-id="55ec9-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="55ec9-132"><xref:System.Windows.Documents.TableCell>může obsahovat jenom elementy, které jsou odvozeny od <xref:System.Windows.Documents.Block>.</span><span class="sxs-lookup"><span data-stu-id="55ec9-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="55ec9-133">Platný podřízené elementy pro <xref:System.Windows.Documents.TableCell> zahrnout.</span><span class="sxs-lookup"><span data-stu-id="55ec9-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <span data-ttu-id="55ec9-134"><xref:System.Windows.Documents.TableCell>elementy nemusí hostovat přímo textového obsahu.</span><span class="sxs-lookup"><span data-stu-id="55ec9-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="55ec9-135">Další informace o členství ve skupině pravidla pro tok obsahu elementy jako <xref:System.Windows.Documents.TableCell>, najdete v části [toku dokumentu přehled](../../../../docs/framework/wpf/advanced/flow-document-overview.md).</span><span class="sxs-lookup"><span data-stu-id="55ec9-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](../../../../docs/framework/wpf/advanced/flow-document-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55ec9-136"><xref:System.Windows.Documents.Table>je podobná <xref:System.Windows.Controls.Grid> element ale k dispozici další možnosti a, proto vyžaduje větší režijní náklady na prostředek.</span><span class="sxs-lookup"><span data-stu-id="55ec9-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="55ec9-137">V následujícím příkladu definuje jednoduché tabulce 2 × 3 s [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="55ec9-137">The following example defines a simple 2 x 3 table with [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="55ec9-138">Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="55ec9-138">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="55ec9-139">![Snímek obrazovky: Vykreslení základní tabulky](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")</span><span class="sxs-lookup"><span data-stu-id="55ec9-139">![Screenshot: Render a basic table](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")</span></span>  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a><span data-ttu-id="55ec9-140">Tabulka členství ve skupině</span><span class="sxs-lookup"><span data-stu-id="55ec9-140">Table Containment</span></span>  
 <span data-ttu-id="55ec9-141"><xref:System.Windows.Documents.Table>odvozená z <xref:System.Windows.Documents.Block> elementu a dodržuje běžné pravidla pro <xref:System.Windows.Documents.Block> elementů na úrovni.</span><span class="sxs-lookup"><span data-stu-id="55ec9-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="55ec9-142">A <xref:System.Windows.Documents.Table> element mohou být obsaženy kterýmkoli z těchto prvků:</span><span class="sxs-lookup"><span data-stu-id="55ec9-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a><span data-ttu-id="55ec9-143">Seskupení řádků</span><span class="sxs-lookup"><span data-stu-id="55ec9-143">Row Groupings</span></span>  
 <span data-ttu-id="55ec9-144"><xref:System.Windows.Documents.TableRowGroup> Element poskytuje způsob, jak nahodile seskupení řádků v tabulce; každý řádek v tabulce musí patřit do seskupení řádků.</span><span class="sxs-lookup"><span data-stu-id="55ec9-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="55ec9-145">Řádky v rámci skupiny řádek často sdílet běžné záměr a může být ve tvaru skupinu.</span><span class="sxs-lookup"><span data-stu-id="55ec9-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="55ec9-146">Běžně používá pro seskupení řádků je oddělení speciální řádky, například název, záhlaví a zápatí řádky, z primární obsahu obsažených v tabulce.</span><span class="sxs-lookup"><span data-stu-id="55ec9-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="55ec9-147">Následující příklad používá [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] definovat tabulku s řádky stylem záhlaví a zápatí stránky.</span><span class="sxs-lookup"><span data-stu-id="55ec9-147">The following example uses [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="55ec9-148">Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="55ec9-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="55ec9-149">![Snímek obrazovky: Tabulky skupin řádků](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="55ec9-149">![Screenshot: Table row groups](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a><span data-ttu-id="55ec9-150">Priorita vykreslování pozadí</span><span class="sxs-lookup"><span data-stu-id="55ec9-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="55ec9-151">V následujícím pořadí (pořadí z-order od nejnižší na nejvyšší) vykreslení elementů tabulky.</span><span class="sxs-lookup"><span data-stu-id="55ec9-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="55ec9-152">Toto pořadí nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="55ec9-152">This order cannot be changed.</span></span> <span data-ttu-id="55ec9-153">Například neexistuje vlastnost "Pořadí vykreslování" pro tyto elementy, které můžete použít k přepsání tohoto pořadí zavedených.</span><span class="sxs-lookup"><span data-stu-id="55ec9-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="55ec9-154">Vezměte v úvahu následující příklad, který definuje barvy pozadí pro každou z těchto elementů v tabulce.</span><span class="sxs-lookup"><span data-stu-id="55ec9-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="55ec9-155">Následující obrázek ukazuje, jak tento příklad vykreslí (pouze barvy pozadí zobrazující).</span><span class="sxs-lookup"><span data-stu-id="55ec9-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="55ec9-156">![Snímek obrazovky: Tabulky z & č. 45; pořadí](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="55ec9-156">![Screenshot: Table z&#45;order](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="55ec9-157">Řádky nebo sloupce</span><span class="sxs-lookup"><span data-stu-id="55ec9-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="55ec9-158">Buněk tabulky může být nakonfigurována rozložit více řádků nebo sloupce s použitím <xref:System.Windows.Documents.TableCell.RowSpan%2A> nebo <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> atributy v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="55ec9-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="55ec9-159">Podívejte se na následující příklad, ve kterém buňku zahrnuje tři sloupce.</span><span class="sxs-lookup"><span data-stu-id="55ec9-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="55ec9-160">Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="55ec9-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="55ec9-161">![Snímek obrazovky: Buňka pokrývání uzlů všechny tři sloupce](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="55ec9-161">![Screenshot: Cell spanning all three columns](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a><span data-ttu-id="55ec9-162">Vytvoří tabulku s kódem</span><span class="sxs-lookup"><span data-stu-id="55ec9-162">Building a Table With Code</span></span>  
 <span data-ttu-id="55ec9-163">Následující příklady ukazují, jak vytvořit prostřednictvím kódu programu <xref:System.Windows.Documents.Table> a jeho naplnění obsah.</span><span class="sxs-lookup"><span data-stu-id="55ec9-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="55ec9-164">Obsah v tabulce jsou rozdělených do pěti řádků (reprezentována <xref:System.Windows.Documents.TableRow> objekty obsažené v <xref:System.Windows.Documents.Table.RowGroups%2A> objekt) a šesti sloupců (reprezentována <xref:System.Windows.Documents.TableColumn> objektů).</span><span class="sxs-lookup"><span data-stu-id="55ec9-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="55ec9-165">Řádky se používají pro účely různých prezentace, včetně názvu řádek má title celou tabulku popisující sloupce dat v tabulce Řádek záhlaví a zápatí řádek s souhrnné informace.</span><span class="sxs-lookup"><span data-stu-id="55ec9-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="55ec9-166">Všimněte si, že znalost problematicky "title", "záhlaví" a "zápatí" řádků nepatří do tabulky; Jedná se o jednoduše řádky s různými charakteristikami.</span><span class="sxs-lookup"><span data-stu-id="55ec9-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="55ec9-167">Buněk tabulky obsahují skutečný obsah, který se může skládat z text, obrázky nebo téměř žádné jiné [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="55ec9-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="55ec9-168">První, <xref:System.Windows.Documents.FlowDocument> je vytvořena na hostitele <xref:System.Windows.Documents.Table>a nový <xref:System.Windows.Documents.Table> je vytvořen a přidán k obsahu <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="55ec9-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="55ec9-169">Další, půl <xref:System.Windows.Documents.TableColumn> objekty jsou vytvořeny a do tabulky přidat <xref:System.Windows.Documents.Table.Columns%2A> kolekce s některé formátování použít.</span><span class="sxs-lookup"><span data-stu-id="55ec9-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55ec9-170">Všimněte si, že v tabulce <xref:System.Windows.Documents.Table.Columns%2A> kolekce používá standardní indexování od nuly.</span><span class="sxs-lookup"><span data-stu-id="55ec9-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="55ec9-171">Řádek název v dalším kroku je vytvořen a přidán do tabulky s některé formátování použité.</span><span class="sxs-lookup"><span data-stu-id="55ec9-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="55ec9-172">Název řádek se stane obsahovat jednu buňku, která zahrnuje všechny šesti sloupce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="55ec9-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="55ec9-173">V dalším kroku se vytvoří a přidat do tabulky řádek záhlaví a buňky v řádku záhlaví jsou vytvořeny a naplněny s obsahem.</span><span class="sxs-lookup"><span data-stu-id="55ec9-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="55ec9-174">V dalším kroku se vytvoří a přidat do tabulky řádek pro data, a v buňkách v tomto řádku jsou vytvořeny a naplněny s obsahem.</span><span class="sxs-lookup"><span data-stu-id="55ec9-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="55ec9-175">Vytváření tento řádek je podobná vytváření řádek záhlaví s použitým formátováním mírně lišit.</span><span class="sxs-lookup"><span data-stu-id="55ec9-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="55ec9-176">Nakonec řádek zápatí vytvářet, přidat a formátovat.</span><span class="sxs-lookup"><span data-stu-id="55ec9-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="55ec9-177">Jako název řádek zápatí obsahuje jednu buňku, která zahrnuje všechny šesti sloupce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="55ec9-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="55ec9-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="55ec9-178">See Also</span></span>  
 [<span data-ttu-id="55ec9-179">Přehled toku dokumentu</span><span class="sxs-lookup"><span data-stu-id="55ec9-179">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [<span data-ttu-id="55ec9-180">Definovat tabulku s XAML</span><span class="sxs-lookup"><span data-stu-id="55ec9-180">Define a Table with XAML</span></span>](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [<span data-ttu-id="55ec9-181">Dokumenty v grafickém subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="55ec9-181">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="55ec9-182">Použít toku obsahu elementy</span><span class="sxs-lookup"><span data-stu-id="55ec9-182">Use Flow Content Elements</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-flow-content-elements.md)
