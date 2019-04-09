---
title: 'Postupy: Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], manipulating FlowDocuments through Blocks property [WPF], , '
- ', '
ms.assetid: cbb7291e-3f1b-433e-9e16-f4d93ced14e8
ms.openlocfilehash: c307d85bf24e2d8a20226856181e0758758d40c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130881"
---
# <a name="how-to-manipulate-a-flowdocument-through-the-blocks-property"></a><span data-ttu-id="a4a0a-102">Postupy: Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks</span><span class="sxs-lookup"><span data-stu-id="a4a0a-102">How to: Manipulate a FlowDocument through the Blocks Property</span></span>
<span data-ttu-id="a4a0a-103">Tyto příklady ukazují některé běžné operace, které lze provést u <xref:System.Windows.Documents.FlowDocument> prostřednictvím <xref:System.Windows.Documents.FlowDocument.Blocks%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a4a0a-103">These examples demonstrate some of the more common operations that can be performed on a <xref:System.Windows.Documents.FlowDocument> through the <xref:System.Windows.Documents.FlowDocument.Blocks%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4a0a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4a0a-104">Example</span></span>  
 <span data-ttu-id="a4a0a-105">Následující příklad vytvoří nový <xref:System.Windows.Documents.FlowDocument> a potom připojí nový <xref:System.Windows.Documents.Paragraph> elementu <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4a0a-105">The following example creates a new <xref:System.Windows.Documents.FlowDocument> and then appends a new <xref:System.Windows.Documents.Paragraph> element to the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksadd)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksadd)]  
  
## <a name="example"></a><span data-ttu-id="a4a0a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4a0a-106">Example</span></span>  
 <span data-ttu-id="a4a0a-107">Následující příklad vytvoří nový <xref:System.Windows.Documents.Paragraph> elementu a vloží na začátek <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4a0a-107">The following example creates a new <xref:System.Windows.Documents.Paragraph> element and inserts it at the beginning of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksinsert)]  
  
## <a name="example"></a><span data-ttu-id="a4a0a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4a0a-108">Example</span></span>  
 <span data-ttu-id="a4a0a-109">Následující příklad získá počet nejvyšší úrovně <xref:System.Windows.Documents.Block> elementů obsažených v <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4a0a-109">The following example gets the number of top-level <xref:System.Windows.Documents.Block> elements contained in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksCount](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblockscount)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblockscount)]  
  
## <a name="example"></a><span data-ttu-id="a4a0a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4a0a-110">Example</span></span>  
 <span data-ttu-id="a4a0a-111">Následující příklad odstraní poslední <xref:System.Windows.Documents.Block> prvek <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4a0a-111">The following example deletes the last <xref:System.Windows.Documents.Block> element in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksremovelast)]  
  
## <a name="example"></a><span data-ttu-id="a4a0a-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4a0a-112">Example</span></span>  
 <span data-ttu-id="a4a0a-113">Následující příklad odebere veškerý obsah (<xref:System.Windows.Documents.Block> elementy) z <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4a0a-113">The following example clears all of the contents (<xref:System.Windows.Documents.Block> elements) from the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksClear](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksclear)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksclear)]  
  
## <a name="see-also"></a><span data-ttu-id="a4a0a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4a0a-114">See also</span></span>

- [<span data-ttu-id="a4a0a-115">Zpracování skupin řádků tabulky prostřednictvím vlastnosti RowGroups</span><span class="sxs-lookup"><span data-stu-id="a4a0a-115">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="a4a0a-116">Zpracování sloupců tabulky prostřednictvím vlastnosti Columns</span><span class="sxs-lookup"><span data-stu-id="a4a0a-116">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
- [<span data-ttu-id="a4a0a-117">Zpracování skupin řádků tabulky prostřednictvím vlastnosti RowGroups</span><span class="sxs-lookup"><span data-stu-id="a4a0a-117">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
