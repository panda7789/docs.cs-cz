---
title: "Postupy: Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks"
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
- 'documents [WPF], manipulating FlowDocuments through Blocks property [WPF], , '
- ', '
ms.assetid: cbb7291e-3f1b-433e-9e16-f4d93ced14e8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f6ea0a1ada69c33a738985c5340aab94453e895
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manipulate-a-flowdocument-through-the-blocks-property"></a>Postupy: Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks
Následující příklady ukazují některé běžných operací, které lze provést na <xref:System.Windows.Documents.FlowDocument> prostřednictvím <xref:System.Windows.Documents.FlowDocument.Blocks%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou <xref:System.Windows.Documents.FlowDocument> a potom připojí nový <xref:System.Windows.Documents.Paragraph> elementu, který chcete <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksadd)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksadd)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří novou <xref:System.Windows.Documents.Paragraph> elementu a vloží ho od začátku <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksinsert)]  
  
## <a name="example"></a>Příklad  
 Získá počet nejvyšší úrovně v následujícím příkladu <xref:System.Windows.Documents.Block> elementů obsažených v <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblockscount)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblockscount)]  
  
## <a name="example"></a>Příklad  
 Následující příklad odstraní poslední <xref:System.Windows.Documents.Block> element v <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksremovelast)]  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere všechny obsahu (<xref:System.Windows.Documents.Block> elementy) z <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksclear)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksclear)]  
  
## <a name="see-also"></a>Viz také  
 [Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [Zpracování sloupců tabulky prostřednictvím vlastnosti Columns](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
