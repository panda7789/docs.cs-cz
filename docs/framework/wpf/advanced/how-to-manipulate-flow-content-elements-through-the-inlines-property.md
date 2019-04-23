---
title: 'Postupy: Zpracování elementů obsahu toku prostřednictvím vlastnosti Inlines'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], manipulating through Inlines property
- documents [WPF], manipulating flow Content elements through Inlines property
- Inlines property [WPF], manipulating flow Content elements
- properties [WPF], Inlines [WPF], manipulating flow Content elements
ms.assetid: 510780d2-3da1-4360-8763-7054bda22ea3
ms.openlocfilehash: cfff958bb4c87e6bfecf2d280224cda233c31806
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186066"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-inlines-property"></a><span data-ttu-id="bdfb0-102">Postupy: Zpracování elementů obsahu toku prostřednictvím vlastnosti Inlines</span><span class="sxs-lookup"><span data-stu-id="bdfb0-102">How to: Manipulate Flow Content Elements through the Inlines Property</span></span>
<span data-ttu-id="bdfb0-103">Tyto příklady ukazují některé běžné operace, které lze provést u vložených elementů obsahu toku (a kontejnery takovýchto prvků, jako například <xref:System.Windows.Controls.TextBlock>) prostřednictvím **Inlines** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bdfb0-103">These examples demonstrate some of the more common operations that can be performed on inline flow content elements (and containers of such elements, such as <xref:System.Windows.Controls.TextBlock>) through the **Inlines** property.</span></span> <span data-ttu-id="bdfb0-104">Tato vlastnost se používá k přidání a odebrání položek z <xref:System.Windows.Documents.InlineCollection>.</span><span class="sxs-lookup"><span data-stu-id="bdfb0-104">This property is used to add and remove items from <xref:System.Windows.Documents.InlineCollection>.</span></span> <span data-ttu-id="bdfb0-105">Tok obsahu prvky dané funkce **Inlines** vlastnosti patří:</span><span class="sxs-lookup"><span data-stu-id="bdfb0-105">Flow content elements that feature an **Inlines** property include:</span></span>  
  
-   <xref:System.Windows.Documents.Bold>  
  
-   <xref:System.Windows.Documents.Hyperlink>  
  
-   <xref:System.Windows.Documents.Italic>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Span>  
  
-   <xref:System.Windows.Documents.Underline>  
  
 <span data-ttu-id="bdfb0-106">Tyto příklady dojde k použití <xref:System.Windows.Documents.Span> jako daný tok obsahu elementu, ale tyto postupy platí pro všechny prvky a ovládací prvky, které hostují <xref:System.Windows.Documents.InlineCollection> kolekce.</span><span class="sxs-lookup"><span data-stu-id="bdfb0-106">These examples happen to use <xref:System.Windows.Documents.Span> as the flow content element, but these techniques are applicable to all elements or controls that host an <xref:System.Windows.Documents.InlineCollection> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdfb0-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdfb0-107">Example</span></span>  
 <span data-ttu-id="bdfb0-108">Následující příklad vytvoří nový <xref:System.Windows.Documents.Span> a pak použije **přidat** spuštěním metody přidat textu jako obsahu podřízené objekty <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="bdfb0-108">The following example creates a new <xref:System.Windows.Documents.Span> object, and then uses the **Add** method to add two text runs as content children of the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
## <a name="example"></a><span data-ttu-id="bdfb0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdfb0-109">Example</span></span>  
 <span data-ttu-id="bdfb0-110">Následující příklad vytvoří nový <xref:System.Windows.Documents.Run> elementu a vloží na začátek <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="bdfb0-110">The following example creates a new <xref:System.Windows.Documents.Run> element and inserts it at the beginning of the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
## <a name="example"></a><span data-ttu-id="bdfb0-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdfb0-111">Example</span></span>  
 <span data-ttu-id="bdfb0-112">Následující příklad získá počet nejvyšší úrovně <xref:System.Windows.Documents.Inline> elementů obsažených v <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="bdfb0-112">The following example gets the number of top-level <xref:System.Windows.Documents.Inline> elements contained in the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesCount](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinescount)]
 [!code-vb[SpanSnippets#_SpanInlinesCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinescount)]  
  
## <a name="example"></a><span data-ttu-id="bdfb0-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdfb0-113">Example</span></span>  
 <span data-ttu-id="bdfb0-114">Následující příklad odstraní poslední <xref:System.Windows.Documents.Inline> prvek <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="bdfb0-114">The following example deletes the last <xref:System.Windows.Documents.Inline> element in the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
## <a name="example"></a><span data-ttu-id="bdfb0-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdfb0-115">Example</span></span>  
 <span data-ttu-id="bdfb0-116">Následující příklad odebere veškerý obsah (<xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="bdfb0-116">The following example clears all of the contents (<xref:System.Windows.Documents.Inline> elements) from the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
## <a name="see-also"></a><span data-ttu-id="bdfb0-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdfb0-117">See also</span></span>

- <xref:System.Windows.Documents.BlockCollection>
- <xref:System.Windows.Documents.InlineCollection>
- <xref:System.Windows.Documents.ListItemCollection>
- [<span data-ttu-id="bdfb0-118">Přehled toku dokumentů</span><span class="sxs-lookup"><span data-stu-id="bdfb0-118">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="bdfb0-119">Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks</span><span class="sxs-lookup"><span data-stu-id="bdfb0-119">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="bdfb0-120">Zpracování sloupců tabulky prostřednictvím vlastnosti Columns</span><span class="sxs-lookup"><span data-stu-id="bdfb0-120">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
- [<span data-ttu-id="bdfb0-121">Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups</span><span class="sxs-lookup"><span data-stu-id="bdfb0-121">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
