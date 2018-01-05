---
title: "Postupy: Sestavení tabulky z programu"
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
helpviewer_keywords: tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fca6a304ea12dd90a71f8718fed5f1595f4cd4b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-table-programmatically"></a><span data-ttu-id="87ea9-102">Postupy: Sestavení tabulky z programu</span><span class="sxs-lookup"><span data-stu-id="87ea9-102">How to: Build a Table Programmatically</span></span>
<span data-ttu-id="87ea9-103">Následující příklady ukazují, jak vytvořit prostřednictvím kódu programu <xref:System.Windows.Documents.Table> a jeho naplnění obsah.</span><span class="sxs-lookup"><span data-stu-id="87ea9-103">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="87ea9-104">Obsah v tabulce jsou rozdělených do pěti řádků (reprezentována <xref:System.Windows.Documents.TableRow> objekty obsažené v <xref:System.Windows.Documents.Table.RowGroups%2A> objekt) a šesti sloupců (reprezentována <xref:System.Windows.Documents.TableColumn> objektů).</span><span class="sxs-lookup"><span data-stu-id="87ea9-104">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="87ea9-105">Řádky se používají pro účely různých prezentace, včetně názvu řádek má title celou tabulku popisující sloupce dat v tabulce Řádek záhlaví a zápatí řádek s souhrnné informace.</span><span class="sxs-lookup"><span data-stu-id="87ea9-105">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="87ea9-106">Všimněte si, že znalost problematicky "title", "záhlaví" a "zápatí" řádků nepatří do tabulky; Jedná se o jednoduše řádky s různými charakteristikami.</span><span class="sxs-lookup"><span data-stu-id="87ea9-106">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="87ea9-107">Buněk tabulky obsahují skutečný obsah, který se může skládat z text, obrázky nebo téměř žádné jiné [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="87ea9-107">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87ea9-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="87ea9-108">Example</span></span>  
 <span data-ttu-id="87ea9-109">První, <xref:System.Windows.Documents.FlowDocument> je vytvořena na hostitele <xref:System.Windows.Documents.Table>a nový <xref:System.Windows.Documents.Table> je vytvořen a přidán k obsahu <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="87ea9-109">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a><span data-ttu-id="87ea9-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="87ea9-110">Example</span></span>  
 <span data-ttu-id="87ea9-111">Další, půl <xref:System.Windows.Documents.TableColumn> objekty jsou vytvořeny a do tabulky přidat <xref:System.Windows.Documents.Table.Columns%2A> kolekce s některé formátování použít.</span><span class="sxs-lookup"><span data-stu-id="87ea9-111">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87ea9-112">Všimněte si, že v tabulce <xref:System.Windows.Documents.Table.Columns%2A> kolekce používá standardní indexování od nuly.</span><span class="sxs-lookup"><span data-stu-id="87ea9-112">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a><span data-ttu-id="87ea9-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="87ea9-113">Example</span></span>  
 <span data-ttu-id="87ea9-114">Řádek název v dalším kroku je vytvořen a přidán do tabulky s některé formátování použité.</span><span class="sxs-lookup"><span data-stu-id="87ea9-114">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="87ea9-115">Název řádek se stane obsahovat jednu buňku, která zahrnuje všechny šesti sloupce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="87ea9-115">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a><span data-ttu-id="87ea9-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="87ea9-116">Example</span></span>  
 <span data-ttu-id="87ea9-117">V dalším kroku se vytvoří a přidat do tabulky řádek záhlaví a buňky v řádku záhlaví jsou vytvořeny a naplněny s obsahem.</span><span class="sxs-lookup"><span data-stu-id="87ea9-117">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a><span data-ttu-id="87ea9-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="87ea9-118">Example</span></span>  
 <span data-ttu-id="87ea9-119">V dalším kroku se vytvoří a přidat do tabulky řádek pro data, a v buňkách v tomto řádku jsou vytvořeny a naplněny s obsahem.</span><span class="sxs-lookup"><span data-stu-id="87ea9-119">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="87ea9-120">Vytváření tento řádek je podobná vytváření řádek záhlaví s použitým formátováním mírně lišit.</span><span class="sxs-lookup"><span data-stu-id="87ea9-120">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a><span data-ttu-id="87ea9-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="87ea9-121">Example</span></span>  
 <span data-ttu-id="87ea9-122">Nakonec řádek zápatí vytvářet, přidat a formátovat.</span><span class="sxs-lookup"><span data-stu-id="87ea9-122">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="87ea9-123">Jako název řádek zápatí obsahuje jednu buňku, která zahrnuje všechny šesti sloupce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="87ea9-123">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="87ea9-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="87ea9-124">See Also</span></span>  
 [<span data-ttu-id="87ea9-125">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="87ea9-125">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
