---
title: "Postupy: Zpracování elementů obsahu toku prostřednictvím vlastnosti bloků"
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
- documents [WPF], manipulating flow content elements through Blocks property
- flow content elements [WPF], manipulating through Blocks property
- properties [WPF], Blocks [WPF], manipulating flow content elements
- Blocks property [WPF], manipulating flow content elements
ms.assetid: aeda4ece-b979-4818-a093-ef938e908751
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d995e9a3a50e733a87a203f94b97a937560a0141
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manipulate-flow-content-elements-through-the-blocks-property"></a><span data-ttu-id="83aa0-102">Postupy: Zpracování elementů obsahu toku prostřednictvím vlastnosti bloků</span><span class="sxs-lookup"><span data-stu-id="83aa0-102">How to: Manipulate Flow Content Elements through the Blocks Property</span></span>
<span data-ttu-id="83aa0-103">Následující příklady ukazují některé běžných operací, které lze provést na toku obsahu prvků prostřednictvím **bloky** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="83aa0-103">These examples demonstrate some of the more common operations that can be performed on flow content elements through the **Blocks** property.</span></span> <span data-ttu-id="83aa0-104">Tato vlastnost se používá k přidání a odebrání položek z <xref:System.Windows.Documents.BlockCollection>.</span><span class="sxs-lookup"><span data-stu-id="83aa0-104">This property is used to add and remove items from <xref:System.Windows.Documents.BlockCollection>.</span></span> <span data-ttu-id="83aa0-105">Tok obsahu elementy této funkce **bloky** vlastnost patří:</span><span class="sxs-lookup"><span data-stu-id="83aa0-105">Flow content elements that feature a **Blocks** property include:</span></span>  
  
-   <xref:System.Windows.Documents.Figure>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.ListItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="83aa0-106">Tyto příklady dojít k použití <xref:System.Windows.Documents.Section> jako tok obsahu elementu, ale tyto postupy platí pro všechny elementy, které jsou hostiteli kolekci tok obsahu elementu.</span><span class="sxs-lookup"><span data-stu-id="83aa0-106">These examples happen to use <xref:System.Windows.Documents.Section> as the flow content element, but these techniques are applicable to all elements that host a flow content element collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83aa0-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="83aa0-107">Example</span></span>  
 <span data-ttu-id="83aa0-108">Následující příklad vytvoří novou <xref:System.Windows.Documents.Section> a použije je **přidat** metody přidat nový odstavec k **části** obsah.</span><span class="sxs-lookup"><span data-stu-id="83aa0-108">The following example creates a new <xref:System.Windows.Documents.Section> and then uses the **Add** method to add a new Paragraph to the **Section** contents.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
## <a name="example"></a><span data-ttu-id="83aa0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="83aa0-109">Example</span></span>  
 <span data-ttu-id="83aa0-110">Následující příklad vytvoří novou <xref:System.Windows.Documents.Paragraph> elementu a vloží ho od začátku <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="83aa0-110">The following example creates a new <xref:System.Windows.Documents.Paragraph> element and inserts it at the beginning of the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksinsert)]  
  
## <a name="example"></a><span data-ttu-id="83aa0-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="83aa0-111">Example</span></span>  
 <span data-ttu-id="83aa0-112">Získá počet nejvyšší úrovně v následujícím příkladu <xref:System.Windows.Documents.Block> elementů obsažených v <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="83aa0-112">The following example gets the number of top-level <xref:System.Windows.Documents.Block> elements contained in the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblockscount)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblockscount)]  
  
## <a name="example"></a><span data-ttu-id="83aa0-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="83aa0-113">Example</span></span>  
 <span data-ttu-id="83aa0-114">Následující příklad odstraní poslední <xref:System.Windows.Documents.Block> element v <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="83aa0-114">The following example deletes the last <xref:System.Windows.Documents.Block> element in the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksremovelast)]  
  
## <a name="example"></a><span data-ttu-id="83aa0-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="83aa0-115">Example</span></span>  
 <span data-ttu-id="83aa0-116">Následující příklad odebere všechny obsahu (<xref:System.Windows.Documents.Block> elementy) z <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="83aa0-116">The following example clears all of the contents (<xref:System.Windows.Documents.Block> elements) from the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksclear)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksclear)]  
  
## <a name="see-also"></a><span data-ttu-id="83aa0-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="83aa0-117">See Also</span></span>  
 <xref:System.Windows.Documents.BlockCollection>  
 <xref:System.Windows.Documents.InlineCollection>  
 <xref:System.Windows.Documents.ListItemCollection>  
 [<span data-ttu-id="83aa0-118">Přehled toku dokumentů</span><span class="sxs-lookup"><span data-stu-id="83aa0-118">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [<span data-ttu-id="83aa0-119">Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups</span><span class="sxs-lookup"><span data-stu-id="83aa0-119">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="83aa0-120">Zpracování sloupců tabulky prostřednictvím vlastnosti Columns</span><span class="sxs-lookup"><span data-stu-id="83aa0-120">Manipulate a Table's Columns through the Columns Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [<span data-ttu-id="83aa0-121">Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups</span><span class="sxs-lookup"><span data-stu-id="83aa0-121">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
