---
title: 'Postupy: Sestavení tabulky z programu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 3848032bf527f64ce591eb2cda98028c835d79f7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371928"
---
# <a name="how-to-build-a-table-programmatically"></a><span data-ttu-id="ef40e-102">Postupy: Sestavení tabulky z programu</span><span class="sxs-lookup"><span data-stu-id="ef40e-102">How to: Build a Table Programmatically</span></span>
<span data-ttu-id="ef40e-103">Následující příklady ukazují, jak prostřednictvím kódu programu vytvořit <xref:System.Windows.Documents.Table> a jeho naplnění obsah.</span><span class="sxs-lookup"><span data-stu-id="ef40e-103">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="ef40e-104">Obsah tabulky jsou rozdělených do pěti řádcích (reprezentované <xref:System.Windows.Documents.TableRow> objekty obsažené v <xref:System.Windows.Documents.Table.RowGroups%2A> objekt) a šest sloupců (reprezentované <xref:System.Windows.Documents.TableColumn> objekty).</span><span class="sxs-lookup"><span data-stu-id="ef40e-104">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="ef40e-105">Řádky se používají pro účely jiné prezentace, včetně titulní řádek určený pro titulek celou tabulku popisující sloupce dat v tabulce Řádek záhlaví a řádek zápatí se souhrnnými informacemi.</span><span class="sxs-lookup"><span data-stu-id="ef40e-105">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="ef40e-106">Všimněte si, že pojem "title", "záhlaví" a "zápatí" řádek nepatří do tabulky; Jedná se o jednoduše řádky s různými charakteristikami.</span><span class="sxs-lookup"><span data-stu-id="ef40e-106">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="ef40e-107">Buňky tabulky obsahují skutečný obsah, který se může skládat z textu, obrázků nebo téměř jakýkoli jiný [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="ef40e-107">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef40e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef40e-108">Example</span></span>  
 <span data-ttu-id="ef40e-109">První, <xref:System.Windows.Documents.FlowDocument> se vytvoří na hostitele <xref:System.Windows.Documents.Table>a nové <xref:System.Windows.Documents.Table> je vytvořen a přidán do obsahu <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="ef40e-109">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a><span data-ttu-id="ef40e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef40e-110">Example</span></span>  
 <span data-ttu-id="ef40e-111">Dále šest <xref:System.Windows.Documents.TableColumn> objekty jsou vytvořen a přidán do tabulky <xref:System.Windows.Documents.Table.Columns%2A> kolekce s některé aplikované formátování.</span><span class="sxs-lookup"><span data-stu-id="ef40e-111">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef40e-112">Všimněte si, že v tabulce <xref:System.Windows.Documents.Table.Columns%2A> kolekce používá standardní indexování od nuly.</span><span class="sxs-lookup"><span data-stu-id="ef40e-112">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a><span data-ttu-id="ef40e-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef40e-113">Example</span></span>  
 <span data-ttu-id="ef40e-114">Titulní řádek v dalším kroku je vytvořen a přidán do tabulky s některé aplikované formátování.</span><span class="sxs-lookup"><span data-stu-id="ef40e-114">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="ef40e-115">Titulní řádek se stane, tak, aby obsahovala jedinou buňku, která překlenuje všechny šest sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="ef40e-115">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a><span data-ttu-id="ef40e-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef40e-116">Example</span></span>  
 <span data-ttu-id="ef40e-117">V dalším kroku řádek záhlaví je vytvořen a přidán do tabulky a buňky v řádku záhlaví jsou vytvořeny a naplněny s obsahem.</span><span class="sxs-lookup"><span data-stu-id="ef40e-117">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a><span data-ttu-id="ef40e-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef40e-118">Example</span></span>  
 <span data-ttu-id="ef40e-119">V dalším kroku řádků dat je vytvořen a přidán do tabulky a buňky v tomto řádku jsou vytvořeny a naplněny s obsahem.</span><span class="sxs-lookup"><span data-stu-id="ef40e-119">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="ef40e-120">Vytváření tento řádek je podobný sestavování řádek záhlaví s mírně odlišné formátování.</span><span class="sxs-lookup"><span data-stu-id="ef40e-120">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a><span data-ttu-id="ef40e-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef40e-121">Example</span></span>  
 <span data-ttu-id="ef40e-122">Nakonec řádek zápatí vytvořili, přidat a ve formátu.</span><span class="sxs-lookup"><span data-stu-id="ef40e-122">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="ef40e-123">V zápatí je uvedené jako titulní řádek obsahuje jedinou buňku, která překlenuje všechny šest sloupců v tabulce.</span><span class="sxs-lookup"><span data-stu-id="ef40e-123">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="ef40e-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef40e-124">See also</span></span>
- [<span data-ttu-id="ef40e-125">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="ef40e-125">Table Overview</span></span>](table-overview.md)
