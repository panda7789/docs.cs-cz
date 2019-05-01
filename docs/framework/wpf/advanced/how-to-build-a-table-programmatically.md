---
title: 'Postupy: Vytvoření tabulky pomocí programu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 315154b37218c0a6845f0a46149fc056780ee650
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051309"
---
# <a name="how-to-build-a-table-programmatically"></a><span data-ttu-id="57753-102">Postupy: Vytvoření tabulky pomocí programu</span><span class="sxs-lookup"><span data-stu-id="57753-102">How to: Build a Table Programmatically</span></span>
<span data-ttu-id="57753-103">Následující příklady ukazují, jak prostřednictvím kódu programu vytvořit <xref:System.Windows.Documents.Table> a jeho naplnění obsah.</span><span class="sxs-lookup"><span data-stu-id="57753-103">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="57753-104">Obsah tabulky jsou rozdělených do pěti řádcích (reprezentované <xref:System.Windows.Documents.TableRow> objekty obsažené v <xref:System.Windows.Documents.Table.RowGroups%2A> objekt) a šest sloupců (reprezentované <xref:System.Windows.Documents.TableColumn> objekty).</span><span class="sxs-lookup"><span data-stu-id="57753-104">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="57753-105">Řádky se používají pro účely jiné prezentace, včetně titulní řádek určený pro titulek celou tabulku popisující sloupce dat v tabulce Řádek záhlaví a řádek zápatí se souhrnnými informacemi.</span><span class="sxs-lookup"><span data-stu-id="57753-105">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="57753-106">Všimněte si, že pojem "title", "záhlaví" a "zápatí" řádek nepatří do tabulky; Jedná se o jednoduše řádky s různými charakteristikami.</span><span class="sxs-lookup"><span data-stu-id="57753-106">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="57753-107">Buňky tabulky obsahují skutečný obsah, který se může skládat z textu, obrázků nebo téměř jakýkoli jiný [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="57753-107">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57753-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="57753-108">Example</span></span>  
 <span data-ttu-id="57753-109">První, <xref:System.Windows.Documents.FlowDocument> se vytvoří na hostitele <xref:System.Windows.Documents.Table>a nové <xref:System.Windows.Documents.Table> je vytvořen a přidán do obsahu <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="57753-109">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a><span data-ttu-id="57753-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="57753-110">Example</span></span>  
 <span data-ttu-id="57753-111">Dále šest <xref:System.Windows.Documents.TableColumn> objekty jsou vytvořen a přidán do tabulky <xref:System.Windows.Documents.Table.Columns%2A> kolekce s některé aplikované formátování.</span><span class="sxs-lookup"><span data-stu-id="57753-111">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57753-112">Všimněte si, že v tabulce <xref:System.Windows.Documents.Table.Columns%2A> kolekce používá standardní indexování od nuly.</span><span class="sxs-lookup"><span data-stu-id="57753-112">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a><span data-ttu-id="57753-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="57753-113">Example</span></span>  
 <span data-ttu-id="57753-114">Titulní řádek v dalším kroku je vytvořen a přidán do tabulky s některé aplikované formátování.</span><span class="sxs-lookup"><span data-stu-id="57753-114">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="57753-115">Titulní řádek se stane, tak, aby obsahovala jedinou buňku, která překlenuje všechny šest sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="57753-115">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a><span data-ttu-id="57753-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="57753-116">Example</span></span>  
 <span data-ttu-id="57753-117">V dalším kroku řádek záhlaví je vytvořen a přidán do tabulky a buňky v řádku záhlaví jsou vytvořeny a naplněny s obsahem.</span><span class="sxs-lookup"><span data-stu-id="57753-117">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a><span data-ttu-id="57753-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="57753-118">Example</span></span>  
 <span data-ttu-id="57753-119">V dalším kroku řádků dat je vytvořen a přidán do tabulky a buňky v tomto řádku jsou vytvořeny a naplněny s obsahem.</span><span class="sxs-lookup"><span data-stu-id="57753-119">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="57753-120">Vytváření tento řádek je podobný sestavování řádek záhlaví s mírně odlišné formátování.</span><span class="sxs-lookup"><span data-stu-id="57753-120">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a><span data-ttu-id="57753-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="57753-121">Example</span></span>  
 <span data-ttu-id="57753-122">Nakonec řádek zápatí vytvořili, přidat a ve formátu.</span><span class="sxs-lookup"><span data-stu-id="57753-122">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="57753-123">V zápatí je uvedené jako titulní řádek obsahuje jedinou buňku, která překlenuje všechny šest sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="57753-123">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="57753-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57753-124">See also</span></span>

- [<span data-ttu-id="57753-125">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="57753-125">Table Overview</span></span>](table-overview.md)
