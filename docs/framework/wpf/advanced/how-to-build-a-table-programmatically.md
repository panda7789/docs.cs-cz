---
title: 'Postupy: Vytvoření tabulky pomocí programu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 9c9061d3c4d6b3de5e1ab42a6b98c20813835ba8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964163"
---
# <a name="how-to-build-a-table-programmatically"></a><span data-ttu-id="4cb43-102">Postupy: Vytvoření tabulky pomocí programu</span><span class="sxs-lookup"><span data-stu-id="4cb43-102">How to: Build a Table Programmatically</span></span>
<span data-ttu-id="4cb43-103">Následující příklady ukazují, jak prostřednictvím kódu programu vytvořit <xref:System.Windows.Documents.Table> a naplnit ho obsahem.</span><span class="sxs-lookup"><span data-stu-id="4cb43-103">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="4cb43-104">Obsah tabulky je rozdělen na pět řádků (reprezentovaných objekty <xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.Table.RowGroups%2A> , které jsou obsaženy v objektu) a <xref:System.Windows.Documents.TableColumn> šesti sloupcích (reprezentované objekty).</span><span class="sxs-lookup"><span data-stu-id="4cb43-104">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="4cb43-105">Řádky se používají pro různé účely prezentace, včetně řádku názvu, který je určený k nadpisu celé tabulky, řádku záhlaví, který popisuje sloupce dat v tabulce a řádek zápatí se souhrnnými informacemi.</span><span class="sxs-lookup"><span data-stu-id="4cb43-105">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="4cb43-106">Všimněte si, že pojem "title", "header" a "Foot" řádky nejsou podstatou tabulky; Jedná se o jednoduché řádky s různými charakteristikami.</span><span class="sxs-lookup"><span data-stu-id="4cb43-106">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="4cb43-107">Buňky tabulky obsahují skutečný obsah, který se může skládat z textu, obrázků nebo téměř jakéhokoliv jiného [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] prvku.</span><span class="sxs-lookup"><span data-stu-id="4cb43-107">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cb43-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cb43-108">Example</span></span>  
 <span data-ttu-id="4cb43-109">Nejprve je vytvořen pro <xref:System.Windows.Documents.Table>hostování a nový <xref:System.Windows.Documents.Table> je <xref:System.Windows.Documents.FlowDocument>vytvořen a přidán do obsahu. <xref:System.Windows.Documents.FlowDocument></span><span class="sxs-lookup"><span data-stu-id="4cb43-109">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a><span data-ttu-id="4cb43-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cb43-110">Example</span></span>  
 <span data-ttu-id="4cb43-111">V dalším kroku <xref:System.Windows.Documents.TableColumn> se vytvoří a přidá šest objektů do <xref:System.Windows.Documents.Table.Columns%2A> kolekce tabulky, přičemž se použije některé formátování.</span><span class="sxs-lookup"><span data-stu-id="4cb43-111">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4cb43-112">Všimněte si, že <xref:System.Windows.Documents.Table.Columns%2A> kolekce tabulky používá standardní indexování založené na nule.</span><span class="sxs-lookup"><span data-stu-id="4cb43-112">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a><span data-ttu-id="4cb43-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cb43-113">Example</span></span>  
 <span data-ttu-id="4cb43-114">V dalším kroku se vytvoří řádek s nadpisem a přidá se do tabulky s některým použitým formátováním.</span><span class="sxs-lookup"><span data-stu-id="4cb43-114">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="4cb43-115">Řádek nadpisu obsahuje jednu buňku, která zahrnuje všechny šest sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="4cb43-115">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a><span data-ttu-id="4cb43-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cb43-116">Example</span></span>  
 <span data-ttu-id="4cb43-117">V dalším kroku se vytvoří řádek záhlaví a přidá se do tabulky a buňky v řádku záhlaví se vytvoří a naplní se obsahem.</span><span class="sxs-lookup"><span data-stu-id="4cb43-117">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a><span data-ttu-id="4cb43-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cb43-118">Example</span></span>  
 <span data-ttu-id="4cb43-119">V dalším kroku se vytvoří řádek pro data a přidají se do tabulky a buňky v tomto řádku se vytvoří a naplní se obsahem.</span><span class="sxs-lookup"><span data-stu-id="4cb43-119">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="4cb43-120">Sestavování tohoto řádku se podobá vytvoření řádku záhlaví s mírně odlišným formátováním.</span><span class="sxs-lookup"><span data-stu-id="4cb43-120">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a><span data-ttu-id="4cb43-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cb43-121">Example</span></span>  
 <span data-ttu-id="4cb43-122">Nakonec se vytvoří, přidá a naformátuje řádek zápatí.</span><span class="sxs-lookup"><span data-stu-id="4cb43-122">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="4cb43-123">Podobně jako u řádku nadpisu obsahuje zápatí jedinou buňku, která zahrnuje všechny šest sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="4cb43-123">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="4cb43-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cb43-124">See also</span></span>

- [<span data-ttu-id="4cb43-125">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="4cb43-125">Table Overview</span></span>](table-overview.md)
