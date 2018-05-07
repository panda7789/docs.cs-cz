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
ms.openlocfilehash: 3bbeac2eda8811939be3c710a8ce28349e7f0759
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-manipulate-flow-content-elements-through-the-inlines-property"></a>Postupy: Zpracování elementů obsahu toku prostřednictvím vlastnosti Inlines
Tyto příklady ukazují některé z nejčastěji operací, které lze provést u vložených elementů obsahu tok (a kontejnerů, které z těchto prvků, jako <xref:System.Windows.Controls.TextBlock>) prostřednictvím **Inlines** vlastnost. Tato vlastnost se používá k přidání a odebrání položek z <xref:System.Windows.Documents.InlineCollection>. Tok obsahu elementy tuto funkci **Inlines** vlastnost patří:  
  
-   <xref:System.Windows.Documents.Bold>  
  
-   <xref:System.Windows.Documents.Hyperlink>  
  
-   <xref:System.Windows.Documents.Italic>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Span>  
  
-   <xref:System.Windows.Documents.Underline>  
  
 Tyto příklady dojít používat <xref:System.Windows.Documents.Span> jako tok obsahu elementu, ale tyto postupy platí pro všechny elementy nebo ovládací prvky, které jsou hostiteli <xref:System.Windows.Documents.InlineCollection> kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou <xref:System.Windows.Documents.Span> objekt a používá **přidat** metoda pro přidání textu se spouští jako obsahu podřízené objekty <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou <xref:System.Windows.Documents.Run> elementu a vloží ho od začátku <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
## <a name="example"></a>Příklad  
 Získá počet nejvyšší úrovně v následujícím příkladu <xref:System.Windows.Documents.Inline> elementů obsažených v <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinescount)]
 [!code-vb[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinescount)]  
  
## <a name="example"></a>Příklad  
 Následující příklad odstraní poslední <xref:System.Windows.Documents.Inline> element v <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere všechny obsahu (<xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Documents.BlockCollection>  
 <xref:System.Windows.Documents.InlineCollection>  
 <xref:System.Windows.Documents.ListItemCollection>  
 [Přehled toku dokumentů](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Zpracování sloupců tabulky prostřednictvím vlastnosti Columns](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
